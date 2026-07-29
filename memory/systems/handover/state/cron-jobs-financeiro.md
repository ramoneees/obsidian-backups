# Cron Jobs Financeiros

> Última atualização: 2026-07-29 (handover).
> Jobs atualmente no perfil `default` (main). Migração para `crisp` é o próximo passo.

## Inventário

| Job ID | Nome | Schedule (UTC) | Lisboa (inverno) | Lisboa (verão) | Status atual |
|---|---|---|---|---|---|
| `470ef7c97cc4` | Firefly Lunch Flow daily sync | `0 1 * * *` | 01:00 | 02:00 | operacional, last_run OK |
| `efb4cf5ea910` | Firefly AI categorizer daily | `15 1 * * *` | 01:15 | 02:15 | operacional, last_run OK |

## Comportamento esperado

- Ambos rodam em `deliver=local` (saída fica em `~/.hermes/profiles/<profile>/cron/output/`).
- O **agent** roda o prompt, que invoca o script Python e parseia o output.
- Prompt do sync verifica: linhas `imported=N target=X cur=Y`, keywords `ERROR`/`FAIL`, e `imported > 0` para awareness.
- Prompt do categoriser verifica: fila resultante, categorias aplicadas vs enfileiradas.

## Por que no perfil crisp (e não no main)

- Crisp é o especialista em finanças. Manter no main significa que Jarvis (main) responde perguntas financeiras, o que contradiz o desenho.
- Cron jobs por perfil permitem que cada agente tenha seu próprio conjunto de rotinas autônomas, isolado do main.
- Scripts em `~/.hermes/scripts/` são **compartilhados no filesystem** (não duplicados), mas o `.env` carregado é o do perfil que está rodando.

## Migração — playbook

```bash
# 1. Pausar job no main
hermes cron update 470ef7c97cc4 --paused

# 2. Criar equivalente no perfil crisp
hermes cron create \
  --profile crisp \
  --name "Firefly Lunch Flow daily sync" \
  --schedule "0 1 * * *" \
  --prompt "..." \
  --script ~/.hermes/scripts/firefly_sync.py \
  --deliver local

# 3. Repetir para o categoriser
# 4. Smoke-test: rodar uma vez e verificar output
# 5. Remover job pausado do main
hermes cron remove 470ef7c97cc4
```

## Caveats

- Cron jobs rodam em UTC no host. Não tente colocar timezone no campo schedule.
- Jobs por perfil rodam sequencialmente (não em paralelo) para manter diretórios isolados.
- `deliver=local` em cron-job não entrega de volta à TUI; apenas salva em `cron/output/`.
- Se Crisp precisar notificar Ramon via Telegram quando algo falhar, usar `deliver=telegram` com `chat_id` apropriado.
