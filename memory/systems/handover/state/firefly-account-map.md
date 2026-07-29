# Firefly — Mapa de Contas

> Última atualização: 2026-07-29 (handover main → Crisp).
> **Ação pendente para Crisp:** auditar via `mcporter call firefly-iii.list_account` e popular com IDs reais.

## Convenções de nomenclatura

- Contas EUR: nome em português, sem código de moeda no nome
- Contas BRL: sufixo `— BRL` quando convivem com EUR同名
- Cartões: prefixo `Cartão `
- Subcontas investimento XP: `XP — <categoria>` (em-dash, espaços)
- Ajustes/sweep: `Ajustes de Saldo` (usada como contraparida em ajustes labeled)

## Playbook para auditar

```bash
# 1. Listar todas as contas Firefly
mcporter call firefly-iii.list_account

# 2. Para cada conta, pegar detalhes (IBAN, role, opening balance)
mcporter call firefly-iii.search_accounts query:"Millennium BCP" field:"name"

# 3. Comparar com a lista de contas Lunch Flow
python3 ~/.hermes/scripts/firefly_sync.py --dry-run
```

## Estrutura esperada (após auditoria)

| Lunch Flow | Firefly account | Role | Notas |
|---|---|---|---|
| 29723 | (a descobrir) | `defaultAsset` BRL | Inter corrente |
| 29719 | (a descobrir) | `defaultAsset` BRL | XP investimentos; eventualmente subaccounts |
| 29721 | (a descobrir) | `defaultAsset` BRL | XP corrente |
| 29720 | (a descobrir) | `ccAsset` BRL | Cartão XP Visa Infinite |
| 29722 | (a descobrir) | `ccAsset` BRL | Cartão Inter |
| — | Millennium BCP Pessoal | `defaultAsset` EUR | IBAN PT50 0033 0000 455574936192 05 |
| — | Revolut EUR Pessoal | `defaultAsset` EUR | spending account |
| — | Revolut GBP Flex Pots | `defaultAsset` GBP | separar um asset account por pot |
| — | Cartão Revolut | `ccAsset` EUR | — |
| — | Ajustes de Saldo | `defaultExpense` | contraparida para reconciliação |

**Não existe conta `defaultLiability`** neste mapa. Todos os cartões são `ccAsset`. Apenas quando uma dívida real aparecer (empréstimo, financiamento) usar `defaultLiability` — não confundir com cartão.
