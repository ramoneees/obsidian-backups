# Mapeamento Lunch Flow — Brasil

> Origem: `obsidian-vault/memory/systems/financeiro.md` (confirmado com Ramon em 2026-07-27).
> Última validação de saldo: 2026-07-27.

## IDs Lunch Flow

| LF ID | Nome exibido | Papel real | Modelo Firefly |
|---:|---|---|---|
| 29723 | Conta Corrente | Inter — conta corrente | `defaultAsset` (BRL) |
| 29719 | XP | Conta de investimentos XP; dividendos caem aqui | `defaultAsset` (BRL) — subaccounts se drift >5% |
| 29721 | XP | Conta corrente XP | `defaultAsset` (BRL) |
| 29720 | Cartão XP Visa Infinite | Cartão de crédito XP; **saldo reportado = saldo devedor**; limite acompanha valor investido | `ccAsset` (BRL) — `credit_card_type=monthlyFull`, `monthly_payment_date=YYYY-MM-DD` |
| 29722 | RAMON CARLOS RIOS | Cartão de crédito Inter; limite total R$ 11.433,59 | `ccAsset` (BRL) — mesma config |

## Saldos observados em 2026-07-27

- Inter corrente (29723): **R$ 445,08**
- XP investimentos/dividendos (29719): **R$ 190,19**
- XP corrente (29721): **R$ 0,00**
- Cartão XP (29720): **R$ 5.542,18 de saldo devedor**
- Cartão Inter (29722): saldo reportado R$ 0,00; **limite total R$ 11.433,59**

## Regras de modelagem (não-violáveis)

1. **Contas correntes e investimentos** são ativos em BRL.
2. **Cartões XP e Inter** são `ccAsset` no Firefly v6.6.6. **Não** interpretar limite como patrimônio ou saldo disponível.
3. **Cartão XP:** saldo da API Lunch Flow é **dívida**, mesmo que positivo. Nunca some ao patrimônio.
4. **Dividendos XP:** caem na conta de investimentos (29719) como **renda de investimentos** — não transferência, não salário. Categoria: investimento/receita, não "Outros".

## Pendências detectadas

- **Subaccounts XP investimentos (29719):** ainda não criadas no Firefly como sub-contas separadas (`XP — Renda Fixa`, `XP — Ações e FIIs`, `XP — Outros Fundos`). Holdings monitoring está em modo **read-only** com warning quando drift >5%. **Não auto-criar sub-contas** sem confirmação explícita.
- **Cartão Inter (29722):** saldo R$ 0,00 mas limite R$ 11.433,59. Limite **não** é patrimônio. Apenas registrar saldo devedor real quando houver fatura.
