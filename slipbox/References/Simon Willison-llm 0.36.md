---
source: "Simon Willison"
title: "llm 0.36"
date: 2026-09-22
url: https://simonwillison.net/2026/Sep/22/llm/
author: "Simon Willison"
category: "Release"
tags: [reference, llm, cli, openai, gpt-6, release]
ingested: 2026-09-23
---

# llm 0.36

**Fonte:** Simon Willison's Weblog (beat post)
**Data:** 22 de setembro de 2026
**URL:** https://simonwillison.net/2026/Sep/22/llm/

## Resumo / notas principais

Release do [llm 0.36](https://github.com/simonw/llm/releases/tag/0.36) — CLI para acessar LLMs pela linha de comando:

- Novos modelos OpenAI: `gpt-6-sol` (GPT-6 Sol) e `gpt-6-luna` (GPT-6 Luna) (#1702).
- Plugins de modelo agora podem declarar `supports_conversation = False` para modelos que só aceitam prompts single-turn. LLM levanta `llm.ConversationNotSupported` quando esses modelos recebem histórico de assistant/tools, e `llm chat` os rejeita antes de iniciar sessão. Primeiro plugin a usar isso: llm-typesafe (#1692).
- Reasoning traces no output Markdown de `llm logs` agora embrulhados em `<details><summary>` (#1701).
- Bug fixes de cinco novos contribuidores.

## Notas e conexões

- Chegou no mesmo dia do anúncio de preço dos novos modelos — [[resumo-claude-opus-5-5-gpt-6-sol-gpt-6-luna-and-a-new-price-war]].
- Série: [[Simon Willison-llm 0.35]] (7 set, gpt-6-astra) e [[Simon Willison-llm 0.34]].
- O padrão `supports_conversation = False` é interessante como design: capability flag declarativa no plugin, erro levantado cedo — útil se o Boss mexer no llm com Qwen/GLM via OpenAI-compat.
