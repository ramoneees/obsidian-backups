---
source: Simon Willison
title: "sqlite-utils 4.1"
author: Simon Willison
date: 2026-07-11
url: https://simonwillison.net/2026/Jul/11/sqlite-utils/
category: technology
tags: [sqlite-utils, sqlite, python, ai-assisted-programming, release-notes, codex]
ingested: 2026-07-12
status: summary
---

# sqlite-utils 4.1

## Fonte

- **Source**: Simon Willison
- **Author**: Simon Willison
- **Published**: 2026-07-11
- **URL**: https://simonwillison.net/2026/Jul/11/sqlite-utils/

## Resumo

Primeiro dot-release desde sqlite-utils 4.0 (lançado dias antes). Traz várias minor features. Padrão da release notes: usar Codex para revisar todas as open issues e destacar as mais fáceis — filosofia do projeto é que a IA fica melhor a cada release para "limpar" o backlog.

### Novidades

- **`sqlite-utils insert` / `upsert` aceitam `--code`**: permite passar bloco de Python (ou path para `.py`) que define `rows()` function ou `rows` iterable como alternativa a importar de file. Extensão óbvia do pattern que já existia em `sqlite-utils convert`. Issue #684.
- **`--type column-name type` em `insert`/`upsert`**: override do tipo auto-escolhido quando tabela é criada. Útil para CSV/TSV com ZIP codes (parecem int mas devem ser TEXT para preservar leading zeros). Issue #131 — feature request de longa data.
- **`table.drop_index(name)` + `sqlite-utils drop-index` command**: drop index by name. Aceita `ignore=True`/`--ignore`. Issue #626.
- **`sqlite-utils query` lê SQL do stdin**: `echo "select * from dogs" | sqlite-utils query dogs.db -`. Issue #765.
- **`sqlite-utils upsert` infere primary key** de tabela existente — `--pk` pode ser omitido. Sugestão do Codex.
- **`table.transform()` / `transform_sql()` aceitam `strict=True`/`False`**: muda SQLite strict mode. Inspirado por [Prefer STRICT tables in SQLite](https://evanhahn.com/prefer-strict-tables-in-sqlite/) por Evan Hahn (que rodou no HN). Implementado via `transform` mechanism que já copia dados entre tabelas. Issues #787.
- **`sqlite-utils transform` aceita `--strict` / `--no-strict`**.

### Workflow com IA que vale destacar

Para implementar strict mode toggling, Simon usou **GPT-5.6 Sol xhigh Codex**. Um dos prompts mais úteis:

> "use uv run python -c and manually exercise the new .transform(strict=) option, see if you can find any edge-cases or bugs"

Efetivamente dizendo ao modelo para **testar manualmente seu próprio trabalho**, fora dos automated tests. Achou dois minor issues que foram fixados.

## Key Takeaways

1. sqlite-utils 4.1 não é major — é housekeeping release, mas o pattern de usar Codex para identificar easy wins é replicável.
2. `--code` option para `insert`/`upsert` fecha gap importante: agora dá para gerar rows programaticamente sem intermediate file.
3. STRICT mode toggle via transform mechanism é a resposta para a limitação que Evan Hahn apontou (não dava para ALTER table para strict, era necessário copiar).
4. O prompt "test your own work outside automated tests" é uma técnica subutilizada com coding agents.