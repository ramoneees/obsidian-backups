---
title: "Qwen 3.8 27B is excellent, but it defaults to wildly overthinking things"
source: "Simon Willison"
date: 2026-08-16
url: "https://simonwillison.net/2026/Aug/16/qwen-38-27b/"
tags: [reference, llms, qwen, local-llms, reasoning, lm-studio]
ingested: 2026-08-17
---

# Qwen 3.8 27B is excellent, but it defaults to wildly overthinking things

**Fonte:** Simon Willison
**Data:** 16 de agosto de 2026
**URL original:** https://simonwillison.net/2026/Aug/16/qwen-38-27b/

## Resumo

Análise hands-on do Qwen 3.8 27B (release de sexta), LLM Apache 2.0 de 27B parâmetros com visão, do lab da Alibaba. Tamanho excelente para laptop bem equipado; predecessor Qwen 3.6 27B era impressionante. Benchmarks self-reported superam tanto o 3.6 27B quanto o closed-weight Qwen 3.7-Plus (um dos melhores de qualquer tamanho até maio) — Simon aguarda benchmarks independentes.

Testado no MacBook Pro 128GB M5 Max e NVIDIA DGX Spark, via LM Studio com o build quantizado Q4_K_M de 17GB (e llama-server no Spark).

## Notas principais

- **O problema do default `xhigh`:** a documentação oficial de `reasoning_effort` define `xhigh` como *default*. "It's a hilarious default." Com o default de contexto de 8.192 tokens do LM Studio, o Qwen queimava tudo pensando em problemas triviais — carregar com o máximo de 262.144 resolve.
- **O experimento pelican:** com xhigh, 21 MINUTOS para gerar o SVG do pelican de bicicleta — 22.276 tokens de raciocínio para 3.223 de output. Resultado: o melhor pelican SVG já gerado localmente (frame certo, duas pernas, asa no guidão, linhas de movimento atrás). "Valeu a pena esperar 21 minutos? Absolutamente not."
- **Sem raciocínio:** mesmo prompt → 3.715 tokens em 137s, qualidade bem inferior. O overthinking produz qualidade real, mas a custo absurdo em hardware de consumidor.
- **"draw an svg of a circle":** com xhigh, o trace de raciocínio debate paletas Bauhaus e prefers-reduced-motion por vários minutos e produz um círculo animado lindíssimo — "entirely not what I had asked for".
- **Recomendação:** ignore o default; rode em `low` ou sem reasoning primeiro. Ótimo modelo, péssimo ponto de partida.
- O post menciona ainda que o modelo é muito bom em bounding boxes (seção cortada nesta extração — completo no cache local).

## Conexões

- Tópicos: [[modelos locais]], [[reasoning effort]], [[Qwen]], [[LM Studio]].
- Mesma semana: [[Simon Willison-Markdown SVG upgrades]] e [[Simon Willison-CORS Chat]] — ferramentas construídas para testar exatamente este modelo.
