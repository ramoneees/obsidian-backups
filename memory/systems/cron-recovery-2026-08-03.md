# Cronjob Recovery 2026-08-03

Diagnóstico e plano de correção para 4 cronjobs quebrados pós-migração Linux → macOS Mini.

## Resumo

15 cronjobs totais. 4 com problema:
- 2 com **status=error** (script quebrado por path Linux hardcoded).
- 2 com **status=ok** mas `delivery_error="no delivery target resolved for deliver=telegram"`.

11 OK sem alterações.

## A — Paths Linux hardcoded ✅ RESOLVIDO

**Causa:** Scripts `daily-note.py` e `weekly-review.py` tinham `VAULT_PATH = "/home/ramoneees/obsidian-vault"`. Em macOS, o path real é `/Users/ramoneees/obsidian-vault`.

**Fix aplicado (2026-08-03):**
```python
# antes
VAULT_PATH = "/home/ramoneees/obsidian-vault"
# depois
VAULT_PATH = os.environ.get("VAULT_PATH") or os.path.expanduser("~/obsidian-vault")
```

Arquivos modificados:
- `~/.hermes/scripts/daily-note.py`
- `~/.hermes/scripts/weekly-review.py`

**Verificação:**
- `daily-note.py` → gerou `/Users/ramoneees/obsidian-vault/dailies/2026-08-03.md`
- `weekly-review.py` → gerou `/Users/ramoneees/obsidian-vault/dailies/reviews/weekly-2026-08-02.md`

## B — fetch_briefing_data.py retornando 0 eventos / 0 tarefas ✅ RESOLVIDO 2026-08-03

**Causa dividida em 2:**

1. **TickTick MCP** — **OK, retorna vazio por estado real** (não tem tasks abertas hoje/next7/last7). Confirmado via `mcporter call ticktick.list_undone_tasks_by_time_query queryCommand=next7day` retornando `{"result": []}`.

2. **Google Calendar MCP** — **OFFLINE por config Linux**. O `~/.mcporter/mcporter.json` aponta:
   ```
   GOOGLE_OAUTH_CREDENTIALS=/home/ramoneees/.openclaw/credentials/google-calendar/gcp-oauth.keys.json
   GOOGLE_CALENDAR_MCP_TOKEN_PATH=/home/ramoneees/.openclaw/credentials/google-calendar/.tokens.json
   ```
   Esses paths não existem em macOS. MCP server falha ao iniciar, mcporter marca como offline, e `mcporter call` retorna connection error.

**Estado dos tokens:**
- `GOOGLE_OAUTH_CREDENTIALS` existe em `~/.hermes/.env` como JSON inline (não como path).
- `GOOGLE_CALENDAR_TOKENS` idem (refresh tokens salvos).
- `~/.hermes/mcp-env.sh` NÃO exporta essas vars pro environment — só passa o que está em `.env` que matcheia nomes hardcoded.

**Decisão:** NÃO modificar OAuth/refresh tokens automaticamente. Risco de trancar conta Google. Plano manual abaixo.

### B.Plano aplicado — Opção A (relocate, sem regenerar OAuth) ✅

1. `mkdir -p ~/.openclaw/credentials/google-calendar/`
2. Extraí JSON de `GOOGLE_OAUTH_CREDENTIALS` do `.env` → `~/.openclaw/credentials/google-calendar/gcp-oauth.keys.json` (chmod 600).
3. Extraí JSON de `GOOGLE_CALENDAR_TOKENS` do `.env` → `~/.openclaw/credentials/google-calendar/.tokens.json` (chmod 600). Tokens têm `personal` + `work`.
4. Backup `~/.mcporter/mcporter.json` → `mcporter.json.bak.2026-08-03`.
5. Editado `mcpServers.google-calendar.env` pra apontar pros paths macOS.
6. Validado: `mcporter list google-calendar` saiu de offline → healthy.
7. `mcporter call google-calendar.list-events ...` retornou eventos reais (Projeto Ramonstro, Psicoterapia, etc.).
8. `python3 fetch_briefing_data.py` retornou 7 eventos, 0 tarefas (TickTick OK, calendário real).

### Aviso adicional

`daily-note.py` reporta warning recorrente:
```
Calendar API falhou: ...google_api.py line 82 TypeError: unsupported operand type(s) for |: 'type' and 'NoneType'
```
**Causa:** Python 3.9 em macOS (Apple CommandLineTools) não suporta `str | None` syntax (PEP 604, requer 3.10+). Script `google_api.py` foi escrito pra Python 3.10+. Não bloqueia o script (cai no except), mas indica que parte do fluxo Calendar não roda. Fix: `from __future__ import annotations` no topo do arquivo, ou rodar com `python3.12`.

## C — Telegram delivery target ✅ RESOLVIDO 2026-08-03

**Jobs afetados:**
- `43b957cc1c77` — Futebol Europeu Semanal (schedule `0 9 * * 1`, segunda 9h)
- `6c4dd9237ac3` — weekly-agenda-briefing (schedule `0 20 * * 0`, domingo 20h)

Ambos com `deliver=telegram`, `last_delivery_error="no delivery target resolved for deliver=telegram"`.

**Causa:** O Briefing Diário (`3f232b9ef9dd`) tem `delivery_error=null` → provavelmente tem chat_id resolvido. Os outros 2 jobs foram criados/copiados e não herdaram o target. O `deliver=telegram` shorthand não resolve para um chat específico sem pareamento explícito.

### C.Plano aplicado

**Achado:** chat_id pareado ativo é `8257687396` (Ramon Rios) — `~/.hermes/pairing/telegram-approved.json`. Briefing Diário continua usando shorthand `deliver=telegram` (resolve OK). Futebol + weekly-briefing com shorthand começaram a falhar "no delivery target resolved" depois da migração Linux → macOS (provavelmente por mudança no estado de pareamento que afetou jobs que não rodavam há semanas).

**Fix aplicado:**
```bash
cronjob update 43b957cc1c77 deliver=telegram:8257687396
cronjob update 6c4dd9237ac3 deliver=telegram:8257687396
```

**Verificação:** `cronjob run 43b957cc1c77` → `last_delivery_error=null`, `executed=true`. (Tive um erro de typo — `8257687696` em vez de `8257687396` — que retornou "Chat not found", mas o chat_id correto do pareamento ativo resolveu na segunda tentativa.)

## Estado dos jobs pós-A

| job_id | name | status atual | observação |
|---|---|---|---|
| bf56842b5803 | Daily Note — Obsidian | error → **deve passar a ok** após próxima run | script consertado; calendar warning persiste |
| b9db496dd76d | Weekly Review — Obsidian | error → **deve passar a ok** após próxima run | script consertado |
| 43b957cc1c77 | Futebol Europeu Semanal | ok mas sem delivery | depende de C |
| 6c4dd9237ac3 | weekly-agenda-briefing | ok mas sem delivery | depende de C |
| 3f232b9ef9dd | Briefing Diário | ok + entrega | funcionando |
| 41cb37c0b2c4 | CouchDB Memory Sync | paused (user abandoned) | não rodar |
| outros 10 | — | ok | sem ação |

## Validação

Após A e antes do próximo cron de hoje (07:00):
- `python3 ~/.hermes/scripts/daily-note.py` deve sair sem FileNotFoundError, gerar daily note.

Após B.plano e C.plano:
- `mcporter call google-calendar.list_events ...` retorna JSON de eventos.
- `cronjob list` mostra os 2 jobs telegram com delivery_error null.

## Open questions

1. Ramon prefere Opção A, B ou C para Calendar? (afeta UX Google — se A falhar, B regenera OAuth client).
2. Ramon prefere Opção 1, 2 ou 3 para Telegram? (afeta UX notificação — fallback local perde push).
