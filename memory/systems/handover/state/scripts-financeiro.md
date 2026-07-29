# Scripts Financeiros

> Última atualização: 2026-07-29.
> Vivem em `~/.hermes/scripts/` (filesystem compartilhado entre perfis).

## Inventário

| Script | Função | Idempotente | Logs |
|---|---|---|---|
| `firefly_sync.py` | Importa saldos + 60d txns do Lunch Flow para Firefly; deduplica por `external_id`; reconcilia cada conta com daily unique id | sim | `~/.hermes/logs/firefly_sync.log` |
| `firefly_categorizer.py` | Categoriza txns sem categoria (deterministic rules → merchant memory → LLM MiniMax) | sim | `~/.hermes/logs/firefly_categorizer.log` |
| `firefly_review.py` | CLI para revisar `/tmp/firefly_review_queue.json` | n/a (interativo) | n/a |
| `categorize_firefly.py` | Bulk one-shot categoriser, **só** para carga inicial | one-shot | n/a |

## State files (load-bearing)

| Arquivo | Função | Backup? |
|---|---|---|
| `/tmp/firefly_sync_state.json` | metadata último sync | regenerável |
| `/tmp/firefly_merchant_memory.json` | comerciante → categoria | **sim, load-bearing** |
| `/tmp/firefly_review_queue.json` | pendentes | regenerável |

## Variáveis de ambiente necessárias (já no `.env`)

- `FIREFLY_URL`
- `FIREFLY_TOKEN` (PAT ou OAuth client_credentials access_token; JWT expira em 24h)
- `INVOICE_NINJA_BASE_URL`
- `INVOICE_NINJA_API_TOKEN`
- `LUNCHFLOW_API_KEY`
- `LITELLM_API_KEY` (se categoriser usar LiteLLM)

## Onde rodam

- Diretamente via `python3 ~/.hermes/scripts/<script>.py`.
- Via cron job (perfis main/crisp).
- Ad-hoc via terminal (`terminal()` do Hermes).

## Pendência

- `categorize_firefly.py` foi usado uma vez para carga inicial. Está obsoleto para operação diária mas mantido como fallback manual. **Não remover** sem confirmar com Ramon.
