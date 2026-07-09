---
source: Simon Willison
title: "Release: llm 0.31.1"
date: 2026-07-09
url: https://simonwillison.net/2026/Jul/9/llm/
category: Release
tags: [llm, cli, bugfix, openai, tooling]
ingested: 2026-07-09
---

# Release: llm 0.31.1

**Source:** Simon Willison's Weblog (beat post)
**Date:** 2026-07-09 16:06 UTC
**URL:** https://simonwillison.net/2026/Jul/9/llm/

## TL;DR

Bugfix pontual em `llm`: tool call com empty arguments nos endpoints OpenAI Chat Completion estava retornando JSON error em alguns providers. Fix associado à issue [#1521](https://github.com/simonw/llm/issues/1521).

## Detalhes

- **Versão:** [llm 0.31.1](https://github.com/simonw/llm/releases/tag/0.31.1)
- **Fix:** empty tool call args → JSON error de alguns providers (issue #1521)
- **Origem do bug:** descoberto testando o plugin `llm-meta-ai` (ver [[Simon Willison-Release- llm-meta-ai 0.1]])

## Notas e Conexões

- Ver [[Simon Willison-Release- llm-meta-ai 0.1]] — o plugin que expôs o bug.
- Ver [[Simon Willison-Introducing Muse Spark 1.1]] — modelo testado que acionou o caminho empty-args.
- Tags do post original: llm.