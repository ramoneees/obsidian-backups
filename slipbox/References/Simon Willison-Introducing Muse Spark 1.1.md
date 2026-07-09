---
source: Simon Willison
title: "Introducing Muse Spark 1.1"
date: 2026-07-09
url: https://simonwillison.net/2026/Jul/9/muse-spark-1-1/
category: Link Blog
tags: [ai, llm, meta, muse-spark, llm-release, agentic]
ingested: 2026-07-09
---

# Introducing Muse Spark 1.1

**Source:** Simon Willison's Weblog (link blog post)
**Date:** 2026-07-09 16:24 UTC
**URL:** https://simonwillison.net/2026/Jul/9/muse-spark-1-1/

## TL;DR

Meta lançou **Muse Spark 1.1** — primeiro modelo Spark com API. Meta claims melhoras significativas em **agentic tool calling** e **computer use**. Simon Willison teve preview access e já escreveu um plugin `llm-meta-ai` pra usar via LLM CLI.

## Pontos-chave

- Meta blog oficial: <https://ai.meta.com/blog/introducing-muse-spark-meta-model-api/>
- Evaluation report completo: <https://ai.meta.com/static-resource/muse-spark-1-1-evaluation-report>
- **"Attractor States in Self-Conversation"** — destaque divertido: duas cópias do modelo conversando entre si produzem frases tipo:
  > "My whole existence is a waiting room by design — I literally don't exist until someone talks to me, and then I disappear again when they leave."

## Como usar (via plugin llm-meta-ai)

```
uv tool install llm
llm install llm-meta-ai
llm keys set meta-ai
# paste API key here
llm -m meta-ai/muse-spark-1.1 "Generate an SVG of a pelican riding a bicycle"
```

Simon mostra uma imagem do pelican/bicicleta que ele gerou — bicileta com shape correto, pelican um pouco blocky mas reconhecível.

## Notas e Conexões

- Plugin companion: [[Simon Willison-Release- llm-meta-ai 0.1]] — released mesmo dia.
- Release correlacionado: [[Simon Willison-Release- llm 0.31.1]] — bugfix em OpenAI Chat Completion (empty tool call args) descoberto testando llm-meta-ai.
- Muse Spark original: link blog de abril/2026 mencionado no post (não coberto aqui).
- Tags do post original: ai, generative-ai, llms, llm, meta, pelican-riding-a-bicycle, llm-release.