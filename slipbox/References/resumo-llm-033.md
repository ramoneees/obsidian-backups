---
title: "Release: llm 0.33"
source: https://simonwillison.net/2026/Aug/22/llm/
date: 2026-08-23
tags: [llm, cli, automacao, ferramentas]
---

# llm 0.33

Nova release do `llm`, o CLI do Simon Willison para acessar LLMs pela linha de comando. O destaque estrutural é a modernização da base: upgrade para a biblioteca OpenAI Python 3.x e troca do cliente HTTP de `httpx` para `httpx2` — conserto definitivo do que o patch 0.32.1 atacou em caráter emergencial.

Em segurança e arquitetura, `llm embed` e `llm embed-multi` agora aceitam `--key` por chamada, e os métodos Python correspondentes aceitam `key=` — a key resolvida passa ao plugin de embedding sem mutar estado compartilhado do modelo. Embeddings passam a usar o mesmo padrão de chaves dos modelos de chat, com fallback de compatibilidade para plugins antigos que leem `self.key`.

A novidade mais elegante é a composição de templates: `-t/--template` pode ser repetido, combinando templates em ordem. Isso destrava o padrão "um template empacota modelo + opções padrão, outro carrega o prompt" — ex.: `llm -m gpt-5.6-luna -o reasoning_effort high --save lhigh`, `llm "..." --save pelican`, e depois `llm -t lhigh -t pelican`. Configuração reutilizável sem código.

Por fim, modelos com reasoning via Responses API ganham `reasoning_summary` (auto/concise/detailed) — útil inclusive para endpoints terceiros que imitam a API da OpenAI, controlar quanto do raciocínio o modelo expõe.

## Por que importa

- Composição de templates é prompt-engineering virando infraestrutura de CLI: encaixa direto na filosofia de automação do Ramon (reprompts e presets sem escrever código).
- O padrão de key por chamada, sem estado compartilhado, é exatamente o que um setup multi-provider exige — relevante para a ponte LiteLLM local (qwen-local → crisp) que ele já mantém.
- `reasoning_summary` com endpoints custom dá controle fino sobre verbosidade de raciocínio ao rotear por modelos próprios.

## Frases notáveis

> "This unlocks a neat pattern where you can create templates that package a model with a set of default options."

> "The embedding models now use the same pattern for keys that regular LLM models do."
