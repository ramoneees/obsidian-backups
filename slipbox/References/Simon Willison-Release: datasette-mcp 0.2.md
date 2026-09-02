---
source: Simon Willison
title: "Release: datasette-mcp 0.2"
author: Simon Willison
date: 2026-09-01
url: https://simonwillison.net/2026/Sep/1/datasette-mcp/
category: release
tags: [datasette, mcp, model-context-protocol, release]
ingested: 2026-09-02
status: summary
---

# Release: datasette-mcp 0.2

## Fonte

- **Source**: Simon Willison (blog, release)
- **Author**: Simon Willison
- **Published**: 2026-09-01
- **URL**: https://simonwillison.net/2026/Sep/1/datasette-mcp/
- **Release**: https://github.com/datasette/datasette-mcp/releases/tag/0.2

## Resumo

Primeira release não-alpha do plugin **datasette-mcp** — adiciona um servidor MCP (`/-/mcp`) a qualquer instância Datasette.

Mudanças na 0.2:
- `rows` do `execute_sql` agora é **array de objetos** (antes: array de arrays) — ajuda modelos mais fracos a não perder o mapeamento entre elemento posicional e coluna (issue #1).
- Dependência: `mcp>=2.1.1`.

Simon usa o plugin bastante ele mesmo — daí a confiança para sair de alpha.

## Key Takeaway

Decisão de API desenhada para consumidores LLM: nomear campos em vez de posição, porque modelos erram menos. Padrão útil para qualquer tool MCP que exponha dados tabulares.
