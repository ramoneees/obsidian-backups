# Sistema financeiro

## Lunch Flow — contas Brasil

Mapeamento confirmado por Ramon em 2026-07-27:

| Lunch Flow ID | Nome exibido | Papel real |
|---:|---|---|
| 29723 | Conta Corrente | Inter — conta corrente |
| 29719 | XP | Conta de investimentos; dividendos caem aqui |
| 29721 | XP | Conta corrente XP |
| 29720 | Cartão XP Visa Infinite | Cartão de crédito XP; saldo reportado é saldo devedor. O limite acompanha o valor investido |
| 29722 | RAMON CARLOS RIOS | Cartão de crédito Inter; limite total R$11.433,59 |

Saldos observados em 2026-07-27:
- Inter corrente: R$445,08
- XP investimentos/dividendos: R$190,19
- XP corrente: R$0,00
- Cartão XP: R$5.542,18 de saldo devedor
- Cartão Inter: saldo reportado R$0,00; limite total R$11.433,59

## Regras de modelagem

- Contas correntes e investimentos: ativos em BRL.
- Cartões XP e Inter: cartões de crédito modelados como asset accounts `ccAsset`; não interpretar limite como patrimônio ou saldo disponível.
- No cartão XP, o saldo do Lunch Flow é dívida, mesmo que positivo na resposta da API.
- Dividendos recebidos na XP investimentos são renda de investimentos, não transferência nem salário.
