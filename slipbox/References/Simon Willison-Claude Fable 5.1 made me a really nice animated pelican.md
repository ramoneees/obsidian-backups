---
source: Simon Willison
title: "Claude Fable 5.1 made me a really nice animated pelican"
author: Simon Willison
date: 2026-09-01
url: https://simonwillison.net/2026/Sep/1/claude-fable-5-1/
category: ai
tags: [claude, fable-5-1, anthropic, llm-reasoning, benchmarks, pelican]
ingested: 2026-09-02
status: summary
---

# Claude Fable 5.1 made me a really nice animated pelican

## Fonte

- **Source**: Simon Willison (blog)
- **Author**: Simon Willison
- **Published**: 2026-09-01
- **URL**: https://simonwillison.net/2026/Sep/1/claude-fable-5-1/

## Resumo

Dia do lançamento **Claude Fable (e Mythos) 5.1** — "novo padrão para coding, knowledge work e tarefas de longa duração". Destaque do anúncio: **52,6% no Terminal-Bench-Science 0.1** (benchmark novo, anunciado 27/ago), contra 24,7% do Fable 5, 29,0% do Opus 5 e 22,4% do GPT-5.6 Sol. Demais benchmarks: melhorias modestas.

Teste de Simon: o pelican benchmark nos **5 níveis de reasoning** do Fable 5.1 (low, medium, high, xhigh, max — sem opção de desligar reasoning):

- **low/medium**: mistério — sem reasoning aparente nos transcripts; ~2.000 tokens output, ~24s, ~10¢ cada.
- **high**: um pouco de reasoning (resumo curto do layout SVG); 2.612 tokens, 13¢.
- **xhigh**: mudança radical — 36.767 tokens, 7min51s, **$1,83**.
- **max**: **o melhor pelican que ele viu de qualquer modelo Anthropic** — 65.927 tokens, 13min54s, **$3,30**. Pernas dos dois lados do quadro, pés nos pedais, asa no guidão, chapelinho azul e cesta com peixe.

Antes disso, corrigiu bug no `llm-anthropic` que não gravava reasoning traces corretamente.

## Key Takeaways

- A escala de custo/tempo entre níveis de reasoning é brutal: mesma tarefa, 10¢ → $3,30 (~30x), 24s → 14 min.
- Insights mais úteis do pelican: comparações **dentro da mesma família** de modelo e **mesmo prompt em níveis de reasoning diferentes**.
- Salto de qualidade real só apareceu em xhigh/max — low/medium aparentemente pularam reasoning para este prompt.
- Simon mantém ceticismo sobre o pelican como proxy geral de capacidade (desde o Kimi K3, jul/2026).
