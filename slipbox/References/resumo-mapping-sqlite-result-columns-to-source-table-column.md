---
title: "Mapping SQLite result columns back to their source table.column"
source: https://simonwillison.net/2026/Jun/13/sqlite-column-provenance/
date: 2026-06-14
tags: [sqlite, python, datasette, dev, automacao]
author: Simon Willison
---

# Mapping SQLite result columns back to their source `table.column`

Simon Willison quer um recurso aparentemente pequeno, mas que destrava um mundo: no **Datasette**, dada uma query SQL arbitrária — incluindo JOINs e CTEs —, identificar programaticamente de qual `tabela.coluna` veio cada coluna do resultado. A motivação é UX: imagine renderizar uma tabela com o nome da tabela de origem em cada cabeçalho, ou aplicar permissões por coluna, ou construir uma UI que "entende" a linhagem dos dados.

A pergunta é não-trivial porque SQL permite renomear, computar, coalescer — mas o SQLite **internamente já sabe** a resposta. Ele calcula a proveniência no momento do `prepare()` do statement, e expõe via `sqlite3_column_table_name()` no C API — só que essa função fica atrás da flag `SQLITE_ENABLE_COLUMN_METADATA` e, crucialmente, **não é exposta pelo módulo `sqlite3` padrão do Python**. (Simon anota de passagem o contexto geopolítico: ele está usando Claude Code Opus 4.8 para a pesquisa, já que o Fable está banido pelo governo dos EUA.)

A solução boa vem do **APSW** (Another Python SQLite Wrapper), o binding "honesto" de Roger Binns: ele expõe `cursor.description_full`, que entrega de cara a proveniência. É a via recomendada para produção, e o código cabe em poucas linhas. Para quem quer ficar em stdlib puro, há um caminho engenhoso: um **bridge via `ctypes`** chamando direto a função C `sqlite3_column_table_name()` — um único arquivo (`column_provenance.py`) faz a costura entre Python e a libsqlite3 carregada dinamicamente. Existe ainda uma terceira via, mais frágil, de **interrogar a saída do `EXPLAIN`** e tentar extrair a info — Simon a descreve como "clever" mas não robusta.

A relevância para o ecossistema Datasette é imediata: significa poder construir ferramentas que tratam SQL como **dado estruturado com linhagem**, não só como stream de linhas. Permissões por tabela, anotações contextuais no front-end, exportação consciente do schema de origem, geração automática de documentação a partir de queries — tudo destrava quando você sabe, para cada célula, de onde ela veio.

## Por que importa

- Para o Ramon (dev/automação): o padrão "module stdlib não expõe isso, mas a lib C tem, então faz bridge com `ctypes`" é exatamente o tipo de **engenharia honesta** que ele valoriza. E o APSW é a alternativa "fazer do jeito certo" — vale lembrar dele para o próximo projeto que precise de mais que o `sqlite3` básico oferece.
- O problema da proveniência de colunas é **genérico em qualquer stack de dados**: o mesmo problema aparece em pipelines ETL, em camadas de BI, em camadas de LLM que precisam citar fontes. A solução de Simon funciona como template mental.
- O uso do Claude Code como "pesquisador junior de APIs" (note o detalhe: "I decided to set Claude Code on the problem") é um caso real de **agente de IA pesquisando internals de C/Python**. Ramon opera com Hermes/OpenClaw — esse padrão (delegar exploração técnica repetitiva a um agente) é diretamente aplicável ao seu setup.

## Frases notáveis

> "Determining the source `table.column` for each result column in arbitrary SQLite queries is feasible because SQLite computes this internally and exposes it via its column-metadata API when compiled with `SQLITE_ENABLE_COLUMN_METADATA`."

> "While Python's standard `sqlite3` module doesn't surface this information, robust methods exist: using the third-party `apsw` library provides direct access with `cursor.description_full`, or a pure-stdlib ctypes bridge can retrieve the data."
