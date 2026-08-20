---
title: "Conceptual integrity and counting lines of code"
source: https://simonwillison.net/2026/Aug/19/conceptual-integrity-and-counting-lines-of-code/
date: 2026-08-20
tags: [ia, engenharia-software, coding-agents, produtividade]
---

## Resumo

Highlights do episódio do Talking Postgres em que Willison entrevista com Claire Giordano sobre como IA está mudando o desenvolvimento de software. Dois argumentos contraintuitivos que merecem registro.

Primeiro: linhas de código *podem* ser métrica de produtividade com coding agents. Um engenheiro produzia ~50-60 linhas de código production-ready por dia (200 num dia excelente). Se agentes permitem mil linhas debugadas com a mesma qualidade — maintainable, testado — isso é melhoria real e mensurável. Mas chegar lá exige a skill e experiência de um engenheiro sênior; o agente não substitui isso.

Segundo, e mais profundo: o gargalo migrou da digitação para a capacidade cognitiva. "Posso produzir código 100x mais rápido, mas não tenho capacidade cognitiva para acompanhar 100x o volume de código." Times continuam necessários para distribuir essa carga cognitiva — não para digitar mais rápido.

E a parte que dá título ao post: conceptual integrity, do *Mythical Man-Month*. Software bem desenhado não tem surpresas, cobre exatamente o domínio certo, tudo se encaixa. Coding agents barateiam tanto adicionar "um quarto novo" que o software cresce com corredores estranhos em direções esquisitas — a analogia da Winchester Mystery House (140 quartos, construída por 40 anos sem plano). A disciplina que antes era imposta pelo custo em semanas agora tem que vir de você: se uma feature maluca custa uma hora em vez de uma semana, é muito mais fácil se justificar.

## Por que importa

- **Disciplina como virtude ativa, não imposta pelo atrito.** A tese de que o custo era o guard-rail e agora o guard-rail é interno é aplicável a qualquer sistema autônomo — pipelines, agentes, hábitos.
- **Cognitive load é o novo gargalo de times de engenharia.** Contratação e arquitetura de times mudam de "velocidade de digitação" para distribuição de compreensão — direto ao interesse em devops e organização de sistemas.
- **"Linhas de código" volta a ser métrica legítima — com caveats.** Argumento raro e bem construído contra o dogma "LOC nunca mede produtividade".

## Frases notáveis

> "I can churn out code a hundred times faster. I don't have the cognitive capacity to stay on top of 100 times the amount of code. So you still need a team of engineers, so you can load balance that cognitive capacity across the team."

> "It's very easy to keep adding new rooms, because the cost of adding those rooms is so much cheaper. What you end up with is something where the conceptual integrity falls apart — and then it's harder to make decisions about it."
