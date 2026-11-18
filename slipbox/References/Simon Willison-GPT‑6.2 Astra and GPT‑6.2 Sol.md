---
title: "GPT‑6.2 Astra and GPT‑6.2 Sol"
source: Simon Willison
date: 2026-11-17
url: https://simonwillison.net/2026/Nov/17/gpt62-astra-and-sol/
author: "Simon Willison"
category: AI / LLM Release
tags: [ia, openai, gpt, llm-pricing, llm-release, pelican-riding-a-bicycle]
ingested: 2026-11-18
blogwatcher_id: 1393
---

# GPT‑6.2 Astra and GPT‑6.2 Sol

**Fonte:** Simon Willison's Weblog | **Data:** 2026-11-17 | **URL:** https://simonwillison.net/2026/Nov/17/gpt62-astra-and-sol/

## Resumo

OpenAI lança dois modelos: **GPT‑6.2 Astra** ("frontier model for your hardest projects") e **GPT‑6.2 Sol** ("efficient, versatile model for everyday work"), disponíveis na API como `gpt-6.2-astra` e `gpt-6.2-sol`. Simon shipou o LLM 0.38 com suporte aos dois. O buzz está misto: Astra 6.2 não alcança o Claude Fable 5.2 nos benchmarks e queixas sobre estilo de comunicação confuso.

## Ideias principais

- **Preços caíram**: Astra 6.2 = $8/MTok input e $40/MTok output (80% do preço do 6 Astra, que era $10/$50) — mesma faixa do Claude Fable 5.2; cached price $0.40/million (vs $1 do anterior), ótimo para sessões agênticas longas
- **Sol mantém preço**: $2/$10 igual ao 6.1 Sol e 6 Sol (metade do GPT-5.6 Sol, $4/$20)
- **Benchmarks de pelican**: Simon rodou o teste do pelican em high/xhigh/max nos dois — comparação visual contra as gerações anteriores
- **Teste prático**: animação Three.js "Yonkers vira mech e pisa em Manhattan" com Ultra effort no Codex CLI — nenhum dos dois morfa o Yonkers bem, abaixo de Claude Fable 5.2 e Gemini 4 Carbon; vídeo comparativo dos dois gerado pelo próprio Astra (Ultra) no app desktop do Codex
- **O exemplo do Theo Browne**: na review pré-lançamento, o modelo gerencia subagents bem em tarefas longas mas pergunta detalhes internos absurdos — "/goal make a new level for Outer Wilds" e 2h depois ele "bloqueia" perguntando qual nome de arquivo o revisor do r24 escreve
- LLM 0.38 já suporta os novos modelos

## Notas e conexões

- Geração anterior da família: [[Simon Willison-The new GPT-5.6 family Luna, Terra, Sol]]
- Sol da rodada anterior e sua estratégia de preço: [[Simon Willison-GPT 6.1 Sol - Near-Astra intelligence for a fifth of the price]]
- Benchmark do pelican com o concorrente direto: [[Simon Willison-Claude Fable 5.1 made me a really nice animated pelican]]
- No mesmo dia, o contra-ponto sobre agentes de código reescrevendo código legado: [[Simon Willison-Quoting Daniel Stenberg]]
- [[slipbox/References]]
