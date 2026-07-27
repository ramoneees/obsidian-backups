# Firefly III + Lunch Flow

Daily synchronisation and AI-assisted categorisation pipeline.

## Cron jobs

| Time (UTC) | Job | What it does |
|---|---|---|
| `0 1 * * *` | `Firefly Lunch Flow daily sync` | Pulls balances and 60 days of transactions from Lunch Flow; reconciles to actual balances. |
| `15 1 * * *` | `Firefly AI categorizer daily` | Runs AI categoriser, applies high-confidence categories, queues low-confidence ones for human review. |

## Scripts

- `~/.hermes/scripts/firefly_sync.py` — Lunch Flow → Firefly import + reconciliation.
- `~/.hermes/scripts/firefly_categorizer.py` — categoriser with three-outcome confidence (CLASSIFIED/ASSUMED/NEEDS_REVIEW).
- `~/.hermes/scripts/firefly_review.py` — interactive CLI to review the queue.
- `~/.hermes/scripts/categorize_firefly.py` — one-shot bulk categorisation (used for the initial pass).

## State files

- `/tmp/firefly_sync_state.json` — last-run metadata.
- `/tmp/firefly_merchant_memory.json` — merchant → category memory.
- `/tmp/firefly_review_queue.json` — pending categorisations.

## Logs

- `~/.hermes/logs/firefly_sync.log`
- `~/.hermes/logs/firefly_categorizer.log`

## Account model (PT)

- Millenium Pessoal (`157`) — EUR, defaultAsset.
- Millenium Empresa (`158`) — EUR, defaultAsset.
- Cash wallet (`159`) — EUR, cashWalletAsset.
- Revolut Pessoal (`160`) — EUR, defaultAsset.
- Revolut Poupança Flexível (`161`) — GBP, savingAsset.
- Cartão Millenium GO (`249`) — EUR, ccAsset, **available**.
- Cartão Millenium Prestige (`251`) — EUR, ccAsset, **available**.
- Cartão Universo (`252`) — EUR, ccAsset, **available**.

## Account model (BR)

- Inter — Conta Corrente (`162`) — BRL.
- XP — Investimentos e Dividendos (`163`) — BRL, legada.
- XP — Conta Corrente (`164`) — BRL.
- XP — Renda Fixa (`253`) — BRL, manual snapshot.
- XP — Ações e FIIs (`254`) — BRL, manual snapshot.
- XP — Outros Fundos (`255`) — BRL, manual snapshot.
- Cartão XP Visa Infinite (`167`) — BRL, ccAsset, **debt**.
- Cartão Inter (`168`) — BRL, ccAsset.

## Categorisation rules

Eight lightweight categories, alphabetically:
Alimentação, Casa e família, Transporte, Saúde e seguros, Serviços e
assinaturas, Impostos e obrigações, Doações e igreja, Outros.

AI fallback: MiniMax-M2.5 via LiteLLM proxy at `10.43.227.167:4000`.

Confidence model:
- `CLASSIFIED` — applied automatically.
- `ASSUMED` — applied automatically.
- `NEEDS_REVIEW` — queued in `/tmp/firefly_review_queue.json`.

Special case: any `Outros` suggestion, regardless of confidence, is
queued for human confirmation. The reasoning is that "Outros" is the
default fallback and shouldn't silently absorb misclassifications.

## Currency & exchange rates

- Daily exchange rates (BRL ↔ EUR ↔ GBP) come from n8n workflow
  `GHoOCyO1zSw4D2be` ("Get Exchange Rate"), triggered daily at 02:00
  Europe/Lisbon.
- Historical rates: query `GET /api/v1/exchange-rates/{FROM}/{TO}`.

## Patching notes

- Firefly deployments may return 404 for
  `POST /api/v1/accounts/{id}/reconcile`; fall back to a labelled
  adjustment transaction.
- The `MiniMax-M2.5` model returns JSON wrapped in a markdown fence
  (` ```json ... ``` `); the categoriser strips the fence before parsing.
- `ccAsset` accounts in Firefly need `credit_card_type` and
  `monthly_payment_date` (use `monthlyFull` and the next month's 1st).
