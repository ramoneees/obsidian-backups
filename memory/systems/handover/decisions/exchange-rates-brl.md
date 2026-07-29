# Decisão: Manter ambos os sentidos EUR↔BRL e EUR↔GBP

> Data: 2026-07-29. Origem: skill `lunchflow-open-banking-sync` § Exchange rates.

## O que manter

Para cada par de moedas presente no ledger (EUR, GBP, BRL), manter **ambas as direções** da cotação:

- `/api/v1/exchange-rates/BRL/EUR` e `/api/v1/exchange-rates/EUR/BRL`
- `/api/v1/exchange-rates/GBP/EUR` e `/api/v1/exchange-rates/EUR/GBP`

## Por que

1. **Firefly usa ambas direções** dependendo do tipo de query (consolidação, relatório, valuation).
2. **Erros de cotação** são detectados pelo teste de reciprocidade (BRL→EUR deve ser o inverso de EUR→BRL dentro de tolerância).
3. **Relatórios consolidados** precisam de pares explícitos, sem inferência on-the-fly.

## Refresh

Daily refresh é apropriado **uma vez que contas BRL/GBP estão incluídas no net worth**. Sem essas contas, refresh sob demanda.

## Caveat: scheduled workflow precisa de defaults explícitos

Quando criar um cron de refresh, **sempre** passar `from` e `to` explícitos. Adicionar schedule direto a um nó HTTP parametrizado sem defaults pode executar com `from/to` vazios.

## Verificação pós-refresh

Após cada refresh, verificar:
1. Cotação da data atual existe.
2. Pares recíprocos coerentes (BRL/EUR × EUR/BRL ≈ 1, dentro de tolerância de FX spread).
