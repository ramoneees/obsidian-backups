---
source: Simon Willison
title: "Release: llm-meta-ai 0.1"
date: 2026-07-09
url: https://simonwillison.net/2026/Jul/9/llm-meta-ai/
category: Release
tags: [llm, meta, muse-spark, plugin, cli, tooling]
ingested: 2026-07-09
---

# Release: llm-meta-ai 0.1

**Source:** Simon Willison's Weblog (beat post)
**Date:** 2026-07-09 16:12 UTC
**URL:** https://simonwillison.net/2026/Jul/9/llm-meta-ai/

## TL;DR

Plugin novo pra [LLM](https://llm.datasette.io/) que dá acesso CLI (e Python library) ao modelo `muse-spark-1.1` da Meta AI API. Lançamento junto com o release do modelo.

## Detalhes

- **Plugin:** [llm-meta-ai](https://github.com/simonw/llm-meta-ai) v0.1
- **Model:** `meta-ai/muse-spark-1.1` (lançado mesmo dia, ver [[Simon Willison-Introducing Muse Spark 1.1]])
- Permite rodar prompts contra o novo modelo via LLM CLI/SDK

## Notas e Conexões

- Ver [[Simon Willison-Introducing Muse Spark 1.1]] — release do modelo + exemplo de uso (`llm -m meta-ai/muse-spark-1.1`).
- Ver [[Simon Willison-Release- llm 0.31.1]] — bugfix no LLM core descoberto testando esse plugin.
- Tags do post original: llm, meta.