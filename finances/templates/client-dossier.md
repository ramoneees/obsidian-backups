# {{CLIENT_NAME}} — Client Dossier

## Identificação

- **Nome:** {{CLIENT_NAME}}
- **NIF:** {{NIF}}
- **Endereço:** {{ADDRESS}}
- **Contacto:** {{EMAIL}} / {{PHONE}}
- **Invoice Ninja ID:** {{INV_NINJA_ID}}
- **Relação desde:** {{DATE}}

## Resumo financeiro

| Métrica | Valor |
|---|---|
| Total faturado YTD | €{{TOTAL_YTD}} |
| Total pendente | €{{TOTAL_PENDING}} |
| Total recebido YTD | €{{TOTAL_PAID}} |
| Invoice mais antiga em aberto | {{OLDEST_OPEN}} |
| Próximo vencimento | {{NEXT_DUE}} |

## Histórico de invoices

| # | Número | Data emissão | Valor | Vencimento | Status | Pago em |
|---|---|---|---|---|---|---|
{{INVOICE_TABLE}}

## Padrões de pagamento

- Prazo médio de pagamento: {{AVG_DAYS}}
- Score de pontualidade: {{SCORE}}/10
- Histórico de atrasos: {{LATE_HISTORY}}

## Notas

{{NOTES}}

---

**Mantido por:** Crisp (auto-atualiza quando sync com Invoice Ninja roda)
**Última atualização:** {{UPDATED_AT}}
