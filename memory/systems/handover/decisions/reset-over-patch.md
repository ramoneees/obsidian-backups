# Decisão: Reset-over-patch quando a reconciliação acumula

> Data: 2026-07-29. Origem: skill `multi-currency-finance-reconciliation` § "When reconciliation debt compounds".

## Quando reconhecer o sinal

A pilha de problemas no ledger que indica hora de reset:

1. **"Ajustes de saldo" genéricos** que mascaram atividade real faltando — não ajuste fino, mas curativo.
2. **Transferências que deveriam ser um único evento two-leg** viraram dois depósitos/saques independentes.
3. **Contas criadas para uso manual** (ex.: `XP — Investimentos e Dividendos`) que depois foram **recortadas em subaccounts** (ex.: `XP — Renda Fixa`, `XP — Ações e FIIs`), deixando histórico órfão.
4. **Drift composto**: cada nova reconciliação arruma a anterior mas introduz uma nova de outro tipo.

## Quando o usuário escolhe reset

Quando o usuário diz "isso está bagunçado demais, vamos resetar" — **concorde, não tente mais um patch cirúrgico**.

## Procedimento de reset

1. **Deletar** todos os transaction groups nas contas em reset (API é confiável; sugerir UI para `expense`/`revenue` que às vezes API não consegue por dependências).
2. **Deletar** as contas via API.
3. **Recriar** contas com a **estrutura correta de primeira vez** — incluindo `ccAsset` para cartões, subaccounts separadas por classe de investimento, etc.
4. **Reimportar** de uma snapshot conhecida de source-of-truth, **NÃO** replayando o histórico bagunçado.

## Por que descartar histórico

É mais barato que cirurgia contínua de reconciliação. O histórico descartado era enganador de qualquer forma.

## Distinção importante

Reset **NÃO é** sinônimo de "começar do zero sem dados". Reset é **reimportar com estrutura correta**. Mantenha o que é real (saldos reais do Lunch Flow, regras de categorização, merchant memory). Descarte o que é resíduo (ajustes genéricos, transferências duplicadas).
