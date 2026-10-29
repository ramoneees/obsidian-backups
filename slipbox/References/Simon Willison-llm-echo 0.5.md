---
title: "llm-echo 0.5"
source: Simon Willison
date: 2026-10-18
url: "https://simonwillison.net/2026/Oct/18/llm-echo/"
author: "Simon Willison"
category: Note
tags: [llm, debug, release, python]
ingested: 2026-10-29
---

# llm-echo 0.5

**Fonte:** Simon Willison | **Data:** 2026-10-18 | **URL:** https://simonwillison.net/2026/Oct/18/llm-echo/

## Resumo

Release 0.5 do llm-echo, plugin de debug do LLM que fornece um "modelo" eco — repete os prompts recebidos sem chamar nenhum LLM.

## Ideias principais

- Novidade: contagens simuladas de token usage agora consideram tool calls, system prompts e reasoning tokens
- Uso típico: testar PRs do LLM sem gastar tokens

## Notas e conexões

- [[slipbox/References]]
