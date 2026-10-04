---
title: "We’re going to need default hard budget caps on pretty much everything"
source: https://simonwillison.net/2026/Oct/3/default-hard-budget-caps/
date: 2026-10-04
tags: [ia, coding-agents, devops, custos]
---

Tese do Willison: serviços pay-as-you-go precisam de hard budget caps como padrão. Depois de $X no mês, o serviço corta e retorna erro. Caps “moles” — aquele email de aviso — não resolvem nada, porque o estrago acontece enquanto você dorme e o email só chega de manhã, junto com a conta.

O contexto que muda tudo: agentes de código derrubaram o atrito para subir código que gasta dinheiro. Chamadas de API paga, hosting, storage que fatura sozinho. O risco de “serviço fugitivo” deixou de ser problema de engenheiro de nuvem e virou risco de qualquer pessoa com um agente pessoal rodando. Preferir erros a uma surpresa de $10.000+ é, para ele, a escolha óbvia.

E o mercado está migrando: a AWS finalmente lançou spend limits (16/09) que pausam o projeto ao atingir o limite mensal, e o Google Cloud já tinha lançado Spend Caps em julho. Willison quer que remover o cap seja opt-in, com um checkbox explícito e assustador: remover o limite de orçamento e assumir responsabilidade pelas cobranças subsequentes.

O fechamento é o mais provocativo: no mundo ideal, os próprios agentes ajudariam — recomendariam provedores com hard caps e avisariam builders iniciantes a não fazer deploy em serviços sem limite.

## Por que importa

- Você roda múltiplos agentes sobre APIs pagas (Hermes, OpenCode, GLM, n8n Gateway com créditos) — exatamente o cenário de agente que gasta enquanto você dorme. Cap duro é o “carinho no gasto” aplicado a infraestrutura.
- Vale auditar quais das suas automações têm limite real configurado versus apenas alerta por email. AWS e GCP agora têm caps nativos — argumento a favor de preferir quem pausa em vez de acumular dívida.
- Provocação de design: ferramentas de agente deveriam tratar “sem cap” como red flag e recomendar provedores limitados por padrão.

## Frases notáveis

> “Soft caps, ‘after $X/month, send me a warning email’, will not cut it.”

> “I expect that most businesses and individuals would prefer errors to a surprise $10,000+ bill.”
