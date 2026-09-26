---
source: "Simon Willison"
title: "Bonsai 2 27B - Near-Lossless Compression in a 9x Smaller Footprint"
date: 2026-09-17
url: https://simonwillison.net/2026/Sep/17/hn-49747390/
author: "Simon Willison"
category: "beat"
tags: [llama-cpp, gguf, modelos-ternarios, local-llm, inferencia]
ingested: 2026-09-26
---

# Bonsai 2 27B — Near-Lossless Compression in a 9x Smaller Footprint

**Fonte:** Simon Willison
**Data:** 17 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/17/hn-49747390/

## Resumo

Comentário do Simon no Hacker News sobre o thread "Bonsai 2 27B: Near-Lossless Compression in a 9x Smaller Footprint" — modelo **ternário** (PTQ) da Prism ML, 27B parâmetros em GGUF de ~5,95 GB. Detalhe prático: os GGUFs oficiais **só funcionam com o fork llama.cpp da Prism** (build `prism-b10685-7dffb15`), não com o llama.cpp upstream.

## Ideias principais

- Receita completa para rodar no macOS arm64: baixar o runtime do release Prism, puxar `Ternary-Bonsai-2-27B-PTQ1_0.gguf` do HF (`prism-ml/Ternary-Bonsai-2-27B-gguf`), servir com `llama-server --port 8331 -ngl 99 -fa on -c 32768`; UI embutida em localhost:8331 ou via API OpenAI-compat com `llm`.
- Performance relatada: ~20 tok/s num M5 Pro (44 tok/s após restart) — mas o servidor avisou `tensor API is not supported in this environment - disabling`, então algo provavelmente não está otimizado.
- Padrão a observar: modelos de compressão extrema (ternários) chegando a forks de runtime — o ecossistema GGUF/llama.cpp como plataforma de testes de quantização agressiva.

## Notas e conexões

- Conecta com [[Simon Willison-Nativ Run AI models locally on your Mac]] e com a skill local do vault para LLMs em Apple Silicon.
- Relevante para a linha "privado→Qwen" do Boss: se ternary 27B em 6 GB se mostra viável, cabe em qualquer Mac — vale testar quando o fork estabilizar.
- [[slipbox/References]]
