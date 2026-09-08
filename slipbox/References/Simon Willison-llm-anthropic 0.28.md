---
title: "llm-anthropic 0.28"
source: "Simon Willison"
date: 2026-09-02
url: "https://simonwillison.net/2026/Sep/2/llm-anthropic/"
category: Release
tags: [reference, llm, anthropic, claude, fable-5-1, release, refusal]
ingested: 2026-09-08
---

# llm-anthropic 0.28

**Fonte:** Simon Willison's Weblog (beat post)
**Data:** 2 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/2/llm-anthropic/

## Resumo / notas principais

Release do [llm-anthropic 0.28](https://github.com/simonw/llm-anthropic/releases/tag/0.28), plugin do `llm` para os modelos da Anthropic (série Claude):

- Suporte ao **Claude Fable 5.1**.
- **Reasoning traces** agora exibidas por padrão nos modelos que as suportam.
- Nova exceção `llm_anthropic.ClaudeRefusal` para quando o Claude responde com um refusal — falha capturável em vez de texto silencioso.

## Notas e conexões

- Mesmo dia de [[Simon Willison-llm 0.34]] e [[Simon Willison-llm-openrouter 0.7.1]].
- Fable 5.1 é o modelo da vez no ciclo Stratechery: [[Stratechery-Write Things Down]] (e o post sobre system prompt anti-letras-de-músicas, 2/set, no weblog do Simon).
- [[slipbox/References]]
