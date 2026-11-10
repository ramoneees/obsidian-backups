---
title: "llm-anthropic 0.31"
source: Simon Willison
date: 2026-11-09
url: https://simonwillison.net/2026/Nov/9/llm-anthropic/
author: "Simon Willison"
category: Beat
tags: [anthropic, claude, llm, llm-release, pelican-riding-a-bicycle]
ingested: 2026-11-10
---

# llm-anthropic 0.31

**Fonte:** Simon Willison | **Data:** 2026-11-09 | **URL:** https://simonwillison.net/2026/Nov/9/llm-anthropic/

## Resumo

Release do plugin llm-anthropic (0.31) adicionando os dois modelos que a Anthropic lançou no dia: **Claude Fable 5.2** e **Mythos 5.2**.

## Ideias principais

- Fable 5.2 estreou em **primeiro lugar** no ranking da Artificial Analysis; a Anthropic diz que ele "resolveu dois problemas abertos na física dos buracos negros" — benchmarks internos ficaram mais ambiciosos
- Uso via LLM: uv tool install llm → llm install llm-anthropic → llm -m claude-fable-5.2 "..."
- Teste dos pelicans nos cinco níveis de reasoning (low, medium, high, xhigh, max): o melhor resultado veio do **xhigh**; o nível **max falhou** em devolver imagem — estourou 128.000 tokens "pensando" sobre eles
- O bug do max não é novo: mesmo comportamento visto no Opus 5.5, mas é novidade na série Fable (Fable 5 e 5.1 devolviam pelicans em max sem problema) — regressão da série nova
- Preço: $8/M input e $40/M output — desconto de 20% sobre o Fable 5.1 ($10/$50)
- Primeiro uso real: ajudar a identificar a fonte de um bip misterioso (ver [[resumo-locating-the-source-of-a-mysterious-beep-with-claude]])

## Notas e conexões

- Comparação de preço com a concorrência: [[Simon Willison-Introducing Our Smallest, Most Efficient Model: Muse Ember]] (Fable 5.2 = 80x o preço dos modelos eficientes)
- Outro teste do modelo no mesmo dia: [[resumo-prompting-claude-fable-52]]
- [[slipbox/References]]
