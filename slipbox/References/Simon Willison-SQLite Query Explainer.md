---
title: "Tool: SQLite Query Explainer"
source: Simon Willison
author: Simon Willison
date: 2026-07-18
ingested: 2026-07-19
url: https://tools.simonwillison.net/sqlite-query-explainer
category: tools
tags: [sqlite, sql, tools, pyodide, simon-willison, julia-evans]
---

# Tool: SQLite Query Explainer

> "Run SQL queries against a SQLite database in your browser and see exactly how SQLite executes them: the tool runs your query, then annotates every line of both `EXPLAIN QUERY PLAN` and the low-level `EXPLAIN` bytecode output with plain-English descriptions."

## TL;DR

Willison construiu um **tool interativo** que roda SQL no navegador (SQLite em Python em Pyodide em WebAssembly) e adiciona **camada de explicação em plain English** aos resultados de `EXPLAIN` e `EXPLAIN QUERY PLAN`. Foi construído por Fable (seu agent). Inspirado por Julia Evans ("Maybe one day I'll learn to read a query plan").

## Contexto

Post de Julia Evans, **"Learning a few things about running SQLite"** ([jvns.ca/blog/2026/07/17/learning-about-running-sqlite/](https://jvns.ca/blog/2026/07/17/learning-about-running-sqlite/)):
> "Maybe one day I'll learn to read a query plan."

Willison concorda ("Big same") e por isso pediu ao **Fable** (agent de coding) para construir o explainer interativo: [PR #299](https://github.com/simonw/tools/pull/299#issue-4919268017).

## Stack técnico

- **SQLite** rodando em Python
- **Python** rodando em **Pyodide**
- **Pyodide** rodando em **WebAssembly**
- Tudo no navegador — sem servidor

Willison adiciona anotações em plain English sobre:
1. `EXPLAIN QUERY PLAN` (high-level: tabela, índice, scan type, join order)
2. `EXPLAIN` (low-level bytecode: virtual machine ops)

## Limitação honesta

Willison admite: "Approach with caution, since I don't know enough about SQLite query plans to verify the results myself, but it seems cromulent enough to me."

Ou seja: a IA (Fable) gerou as anotações, e Willison não tem expertise suficiente em query plans para auditá-las completamente. **Confiança calibrada**.

## Notas e Conexões

- Tags Willison: `sql`, `sqlite`, `tools`, `julia-evans`, `pyodide`, `claude-mythos-fable`
- Willison classifica como **beat** (note curto, não link blog)
- Conexão direta com [[SQLite Query Optimization]] ou notas sobre SQLite no vault
- Conexão com [[Fable]] — agent que Willison usa para construir ferramentas
- Conexão com [[Julia Evans]] — referência recorrente no blog do Willison
- O codebase do tool é público em [github.com/simonw/tools](https://github.com/simonw/tools)
