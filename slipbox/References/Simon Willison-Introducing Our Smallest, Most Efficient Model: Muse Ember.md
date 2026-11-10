---
title: "Introducing Our Smallest, Most Efficient Model: Muse Ember"
source: Simon Willison
date: 2026-11-10
url: https://simonwillison.net/2026/Nov/10/muse-ember/
author: "Simon Willison"
category: Link post
tags: [llm-pricing, meta, llm-release, artificial-analysis, benchmark]
ingested: 2026-11-10
---

# Introducing Our Smallest, Most Efficient Model: Muse Ember

**Fonte:** Simon Willison | **Data:** 2026-11-10 | **URL:** https://simonwillison.net/2026/Nov/10/muse-ember/

## Resumo

Link post sobre o lançamento do Muse Ember, entrada da Meta AI na categoria dos modelos pequenos/rápidos (Claude Haiku / GPT Luna). O Simon analisa sobretudo o **preço** e o posicionamento de eficiência.

## Ideias principais

- Descrição da Meta: menor e mais eficiente modelo, feito para "execução de raciocínio complexo e o trabalho que agentes repetem o dia todo": tool calls, subtasks de código, routing, extração, parsing de documentos longos
- Preço em prompts curtos iguala GPT-6 Luna e Claude Haiku 5.5: $0.10/M input e $0.50/M output — enquanto Claude Fable 5.2 (ver [[Simon Willison-llm-anthropic 0.31]]) custa 80x isso ($8/$40)
- Com prompts longos os thresholds divergem: Luna até 272k tokens ($0.20/$0.75 acima), Ember até 200k ($0.30/$1.50 acima), Haiku até 100k ($0.50/$2.50 acima) — Ember fica entre os dois; cached input da Ember é o mais barato ($0.004/M)
- Preço-por-token perdeu sentido na era de reasoning tokens (modelos usam quantidades muito diferentes para o mesmo problema) — a medida útil é o Intelligence Index vs. Cost per Task da Artificial Analysis
- Muse Ember senta na **linha de Pareto** do leaderboard: "nenhum modelo pontua mais alto por menos por tarefa"; o Simon nota que GPT-6.1 Terra (low) também está na fronteira — "claramente deveria prestar mais atenção à família Terra"
- Seis níveis de reasoning (minimal, low, medium, high, xhigh, max); teste dos pelicans de bicicleta: nível "high" falhou em devolver o SVG completo e a qualidade visual não mapeou linearmente com o nível — pelicans do Ember comparáveis aos do Muse Wonder, que custa 40x mais

## Notas e conexões

- Fable 5.2 citado como contraponto de preço: [[Simon Willison-llm-anthropic 0.31]] (lançamento no mesmo dia) e [[resumo-prompting-claude-fable-52]]
- [[slipbox/References]]
