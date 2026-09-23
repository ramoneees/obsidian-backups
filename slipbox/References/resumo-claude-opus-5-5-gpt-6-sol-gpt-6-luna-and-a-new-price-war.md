---
title: "Claude Opus 5.5, GPT-6 Sol, GPT-6 Luna, and a new price war"
source: https://simonwillison.net/2026/Sep/22/opus-and-sol-and-luna/
date: 2026-09-23
tags: [ia, llm, precos, agentes]
---

Em 24h saíram Grok 4.7, MiMo v2.6, Claude Opus 5.5 e GPT-6 Sol + Luna. O conteúdo real da notícia não é a quantidade de modelos — é o preço. GPT-6 Luna caiu para $0.10/M de input e $0.50/M de output, metade do que o GPT-5.6 Luna (que já era barato) custava. Sol teve corte similar. Com o aumento agendado de 25% no GPT-5.6 para novembro, o GPT-6 está na prática a um quarto do preço.

A Anthropic respondeu: Opus 5.5 custa $4/$20 (20% menos que a família Opus anterior) e, mais relevante para uso agêntico, cache read caiu 60% ($0.20/M). Como 90%+ dos tokens de input em conversas agênticas longas são cobrados como cache, isso muda a economia real de sessões de coding-agent.

O melhor do post é o teste de estresse involuntário: no "pelican riding a bicycle", Opus 5.5 no nível de thinking "max" pensou tanto que estourou o teto de 128k tokens de output sem nunca devolver a resposta — duas vezes, $2.56 e ~20 minutos cada. Willison conclui que "max" é efetivamente inútil: se o modelo over-thinka até quebrar num prompt idiota, não confia nele para trabalho sério. Fable 5.1 em "max", por contraste, entregou o melhor pelican que ele já viu de um modelo Anthropic.

Estado atual dele: GPT-6 Sol e Opus 5.5 como defaults em Codex e Claude Code; o demo Datasette Agent rodando em GPT-6 Luna, rápido e competente.

## Por que importa

- Cache a -60% muda o custo dos agentes em produção (OpenCode, Hermes, pipelines CI) — hora de recalcular qual modelo é o default de cada tarefa.
- Guerra de preços derrubou o piso: Luna a $0.10/$0.50 abre espaço para rodar tarefas mecânicas em modelo frontier sem culpa.
- O caso do "max" é lição prática: nível máximo de reasoning não é monotônico — mais pensamento pode significar resposta que nunca chega, e você paga por isso.

## Frases notáveis

> "It's hard to overstate how competitive this pricing is."

> "This makes me suspect that 'max' is effectively useless — if it over-thinks to breaking point on a stupid SVG prompt I don't trust it not to do the same for more interesting work."
