---
title: "llm-tools-datasette 0.1.1"
source: Simon Willison
date: 2026-10-18
url: "https://simonwillison.net/2026/Oct/18/llm-tools-datasette/"
author: "Simon Willison"
category: Note
tags: [llm, datasette, release, python]
ingested: 2026-10-29
---

# llm-tools-datasette 0.1.1

**Fonte:** Simon Willison | **Data:** 2026-10-18 | **URL:** https://simonwillison.net/2026/Oct/18/llm-tools-datasette/

## Resumo

Release 0.1.1 do llm-tools-datasette: correção da quebra causada quando o LLM 0.33 migrou para httpx2 — plugins que usavam httpx sem depender diretamente dele quebraram, este foi um deles.

## Ideias principais

- Lição de versionamento: dependência transitiva implícita quebrou plugins no upgrade do core

## Notas e conexões

- [[slipbox/References]]
