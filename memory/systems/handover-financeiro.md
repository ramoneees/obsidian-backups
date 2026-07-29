# Handover Financeiro — main → Crisp

> **Estado em:** 2026-07-29
> **Origem:** perfil `default` (main) onde a stack financeira foi montada entre Jun–Jul 2026
> **Destino:** perfil `crisp` (`@CrispRamoneeesBot`, MiniMax-M2.7)
> **Autor desta nota:** Jarvis (main), durante a sessão de handover

## Por que existe este documento

Crisp é o agente especialista em finanças. Até agora, no entanto, era o perfil `default` (Jarvis) que operava o pipeline Firefly ↔ Lunch Flow, o categoriser, e a reconciliação multi-moeda. Esta nota consolida o estado do trabalho para Crisp assumir a operação sem lacunas.

## TL;DR para Crisp

1. **Sistemas canônicos:** Firefly III (ledger) + Lunch Flow/Pluggy (bank truth) + Invoice Ninja (receivables). Não invente um quarto sistema.
2. **Pipeline diário já roda:** `firefly_sync.py` (01:00 UTC) + `firefly_categorizer.py` (01:15 UTC). Hoje operam no perfil main; **estão sendo movidos para o perfil Crisp**.
3. **Cinco contas BRL confirmadas** (mapeamento Ramon, 2026-07-27). Ver `state/lunchflow-mapping-brasil.md`.
4. **Multi-moeda real:** EUR (Millennium/Revolut/Moey), GBP (Revolut flex pots), BRL (Inter/XP). **Não force 1:1.**
5. **Cartões = `ccAsset`** no Firefly v6.6.6. NÃO tente `liability_type: Debt` — API rejeita.
6. **Regra contabilista é lei:** `MM_YYYY_TIPO_Emitente.pdf`. Tipos FT/ND/NC/FS/EX/NL/REC. Data de **emissão**, não pagamento. Integra com Octa Manager.

## Índice do handover

| Documento | Conteúdo |
|---|---|
| `state/lunchflow-mapping-brasil.md` | IDs Lunch Flow das 5 contas BRL + saldos verificados + regras de modelagem |
| `state/lunchflow-mapping-europa.md` | (a criar) Contas EUR/GBP e suas particularidades |
| `state/firefly-account-map.md` | (a criar) Mapeamento Lunch Flow → conta Firefly + role de cada uma |
| `state/cron-jobs-financeiro.md` | Lista dos cron jobs movidos + horários UTC vs Lisbon |
| `state/scripts-financeiro.md` | Inventário dos scripts em `~/.hermes/scripts/` |
| `decisions/regra-categorizacao-outros.md` | Por que `Outros` é confirmation gate, não resposta final |
| `decisions/reconciliacao-stale-adjustments.md` | Por que deletamos `Reconciliação …` do dia antes de postar nova |
| `decisions/reset-over-patch.md` | Quando preferir reset completo a patch cirúrgico |
| `decisions/exchange-rates-brl.md` | Por que manter ambos os sentidos EUR↔BRL e EUR↔GBP |

## Princípios operacionais (não negociáveis)

### 1. Confrontar → plano → executar → reconciliar
Ramon quer ser confrontado antes de mudanças amplas. "Cria tudo" significa aceleração, **não bypass de revisão**. Workflow padrão: confrontar primeiro; depois plano explícito; só então executar; reconciliar por fim.

### 2. Bloqueios honestos, nunca balances inventados
Se uma API falhar ou uma cotação faltar, **diga o bloqueio**. Não invente saldo, não invente FX, não infira pote Revolut sem dados reais. Quando *necessário* usar saldo inferido, documente explicitamente em `notes` da conta que o número é stand-in.

### 3. Idempotência sempre
Todo script precisa sobreviver a rerun e a crash mid-run:
- `external_id` estável e único (`lunchflow:<lfid>:<txid>` para txns, `lunchflow-reconcile:lf:<lfid>:<YYYY-MM-DD>` para ajustes)
- Reconhecer formatos legados ao ler (aceitar o último segmento após `:` como bare Lunch Flow ID)
- Deletar `Reconciliação …` do mesmo dia antes de postar nova — senão reruns deixam a conta off-by-previous-adjustment
- Crash mid-write é aceitável; o próximo run retoma do último external_id persistido

### 4. Categorização: 5–8 grupos, "ask first time"
Lista canônica atual:
- Alimentação
- Casa e família
- Saúde
- Transporte
- Serviços e assinaturas
- Lazer
- Trabalho
- Outros *(confirmation gate, não bucket final)*

**Regra de "Outros":** se o categoriser chega em `Outros` para um comerciante novo, **NÃO auto-aplique** mesmo que o modelo retorne `CLASSIFIED`. Coloque na review queue. Quando o usuário aprovar uma vez, persista em `merchant_memory` para a próxima ser automática.

### 5. Transferências nunca são despesa
- Transferência entre contas próprias: `transfer` único, `external_id` matched, suprimir a perna duplicada
- FX funding (Revolut EUR → Inter BRL): duas pernas nativas (EUR + BRL), `tag: fx-funding` compartilhado; **só invente a perna faltante se a outra existir com divergência <1%**
- Pagamento de cartão: settlement, não nova despesa
- Compra no cartão: aumenta dívida/negativo do `ccAsset`; **conte só o pagamento ao merchant final**

## Estado dos artefatos

### Skills (em migração para Crisp)

| Skill | Local atual | Estado |
|---|---|---|
| `firefly-pipeline` | `~/.hermes/skills/financeiro/firefly-pipeline/SKILL.md` | madura, operacional |
| `lunchflow-open-banking-sync` | `~/.hermes/skills/finance/lunchflow-open-banking-sync/SKILL.md` | madura, referências em `references/` |
| `multi-currency-finance-reconciliation` | `~/.hermes/skills/finance/multi-currency-finance-reconciliation/SKILL.md` | madura, com refs de account-map e fx-pairing |
| `firefly-iii-account-reconciliation` | `~/.hermes/skills/firefly-iii-account-reconciliation/SKILL.md` | consolidada, com pitfall PAT vs JWT + OAuth client_credentials |

**Ação:** mover para `~/.hermes/profiles/crisp/skills/` e arquivar cópias globais em `.archive/`.

### Scripts (filesystem compartilhado)

Vivem em `~/.hermes/scripts/` (não são por perfil):

| Script | Função |
|---|---|
| `firefly_sync.py` | Importa saldos + 60d txns do Lunch Flow, deduplica por external_id, reconcilia cada conta |
| `firefly_categorizer.py` | Categoriza txns sem categoria (deterministic → memory → LLM) |
| `firefly_review.py` | CLI de review (`show`, `apply`, `edit <gid> <cat>`, `skip`, `clear`, `interactive`) |
| `categorize_firefly.py` | Bulk categoriser one-shot (só usado na carga inicial) |

### State files

| Arquivo | Função |
|---|---|
| `/tmp/firefly_sync_state.json` | metadata do último sync (re-entrância) |
| `/tmp/firefly_merchant_memory.json` | comerciante → categoria (versionado, load-bearing — backupe antes de migrações) |
| `/tmp/firefly_review_queue.json` | pendentes para revisão humana |

### Logs

| Arquivo | Função |
|---|---|
| `~/.hermes/logs/firefly_sync.log` | append-only, ISO-8601 |
| `~/.hermes/logs/firefly_categorizer.log` | append-only |

### Cron jobs (em migração para Crisp)

| Job ID atual | Nome | Schedule UTC | Próxima ação |
|---|---|---|---|
| `470ef7c97cc4` | Firefly Lunch Flow daily sync | `0 1 * * *` | mover para perfil crisp |
| `efb4cf5ea910` | Firefly AI categorizer daily | `15 1 * * *` | mover para perfil crisp |

Em horário Lisboa (DST-aware): sync ~02:00, categoriser ~02:15.

## Caveats conhecidos

1. **Firefly v6.6.6 — `category_name` falso negativo:** a API retorna `"Outros"` mesmo após `PUT` que omite category. Use `t.get("category") is None` para detectar falta real. Para limpar, force `category_id: null` explícito no payload.

2. **LiteLLM `MiniMax-M2.5/M2.7` retorna JSON em fence markdown.** `response_format: json_object` é silenciosamente ignorado. Sempre strip fence com regex antes do `json.loads`.

3. **Token Firefly: PAT vs JWT.** UI v6+ sempre gera JWT (~24h). Para automação de longa duração, **OAuth2 `client_credentials`** dá `expires_in: 31536000` (1 ano). O `client_secret` é secret de longa duração — nunca cole em chat, use `read -s`.

4. **Reconciliação via API pode 404.** Fallback: transação labeled `Reconciliação …` com `external_id` único-por-dia. Lembre de **deletar a antiga** antes de postar a nova no mesmo dia.

5. **`ccAsset` echo incompleto.** A criação sucede mas a resposta pode dropar `credit_card_type` e `monthly_payment_date`. Sucesso na criação = suficiente, não o echo.

6. **Lunch Flow high-volume: chunkar 15 dias.** Chamadas únicas de 60 dias truncam ~65k chars em contas com round-ups densos (Revolut spending).

7. **Revolut round-up pots (To/From Fundos de investimento flexíveis):** pernas expostas em EUR; o cash real é GBP. **Não importe em nenhum dos lados como transação Firefly.** Reconsilie o pot GBP contra saldo real quando conhecido.

8. **Holdings XP via Pluggy:** exibe só `MUTUAL_FUND`/`FIXED_INCOME_FUND`/`EQUITY` parcial. **Não auto-reconcilie** subaccounts vs holdings; se drift >5%, log warning e saia com código não-zero; usuário reconcilia manualmente com extrato da corretora.

9. **Sandbox do TUI:** `/tmp` e env vars **não persistem entre chamadas `execute_code`** — use `terminal()` direto para one-liners.

10. **execute_code BLOCKED:** se 2+ timeouts consecutivos "BLOCKED: timed out", pare de usar `execute_code` no turno, troque para `terminal()` `python3 -c`.

## Próximos passos (já definidos, mas ainda não executados)

- [x] Pré-popular `~/.hermes/profiles/crisp/memories/MEMORY.md` e `USER.md` com o consolidado
- [x] Copiar 4 skills para `~/.hermes/profiles/crisp/skills/` e arquivar globais em `.archive/`
- [x] Resolver armadilha do scheduler: cron jobs no Hermes são globais (storage `~/.hermes/cron/jobs.json`, sem campo `profile`). Solução escolhida: **adicionar `skills.external_dirs: [~/.hermes/profiles/crisp/skills]` em `~/.hermes/config.yaml`** (default profile). Scheduler do main carrega as skills via external_dirs; fonte canônica segue única no perfil Crisp.
- [x] Recriar cron jobs `9952d3867eb3` (sync 01:00) e `e1c9f49b2167` (categoriser 01:15) no scheduler global
- [x] Remover jobs antigos `470ef7c97cc4` e `efb4cf5ea910` do default
- [ ] Smoke-test: rodar `firefly_sync.py` uma vez via Crisp e verificar output vs baseline — **pendente**
- [ ] Validar cron `next_run_at` após migração — **pendente primeira execução às 02:00 Lisboa de 2026-07-30**

## Histórico do handover

| Data | Quem | O que |
|---|---|---|
| 2026-07-29 | Jarvis (main) | Criou este documento; consolidou estado para migração |
| 2026-07-29 | Jarvis (main) | Executou migração: handover docs, MEMORY/USER Crisp, 4 skills → `profiles/crisp/skills/`, external_dirs configurado, cron jobs movidos para scheduler global com skill `firefly-pipeline`/`multi-currency-finance-reconciliation` |
