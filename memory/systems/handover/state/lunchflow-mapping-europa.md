# Mapeamento Lunch Flow — Europa

> Status: **incompleto**. Última consolidação: 2026-07-29 (handover main → Crisp).
> Crisp precisa auditar e preencher este documento antes de mexer nas contas europeias.

## Contas confirmadas (não-drift)

Detalhe de cada conta, saldos e particularidades devem ser extraídos dos logs Firefly + Lunch Flow via `firefly_sync.py --dry-run` ou inspeção manual. Antes de popular, valide com Ramon quais contas estão ativas e quais são legadas.

## Particularidades regionais a preservar

### Revolut (multi-moeda)
- **Spending account EUR:** transações vêm como EUR, mas round-ups (`To/From Fundos de investimento flexíveis`) expõem a perna em EUR enquanto o cash real vai para pot GBP. **Não importe as duas pernas como transação Firefly** — pule e reconcilie o pot GBP contra saldo real.
- **Pots GBP flexíveis:** modelados como `defaultAsset` em GBP separados. Lunch Flow pode expor apenas o saldo da spending account; para o pot, documente saldo inferido se necessário, **nunca invente histórico FX**.

### Millennium BCP (EUR)
- Conta corrente pessoal EUR.
- IBAN atualizado 2026-04: `PT50 0033 0000 45574936192 05` (com espaços visuais) — store no Firefly account_number com espaços; iban com ou sem espaços (escolha consistente).

### Moey / Revolut Pessoal
- Provavelmente outra conta EUR pessoal.
- Confirmar com Ramon antes de adicionar novas contas.

### Cartão Revolut / outros cartões EUR
- Modelar como `ccAsset` (não liability) no Firefly v6.6.6.
- **Não usar `liability_type: "Debt"`** — API rejeita mesmo que a UI mostre essa opção.
- Sucesso na criação = suficiente, mesmo que `credit_card_type`/`monthly_payment_date` sumam do echo.

## Próximo passo para Crisp

1. Rodar `python3 ~/.hermes/scripts/firefly_sync.py --dry-run` para listar todas as contas Lunch Flow ativas.
2. Para cada uma, mapear para conta Firefly existente (search por nome).
3. Preencher este documento com IDs, papéis, saldos correntes.
4. Se houver conta nova, seguir o playbook "Adding a new account" em `firefly-pipeline/SKILL.md`.
