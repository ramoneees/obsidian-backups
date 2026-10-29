---
title: "sparqlite: SPARQL 1.1 inside SQLite, written in Rust"
source: Simon Willison
date: 2026-10-16
url: "https://simonwillison.net/2026/Oct/16/sqlite-sparql-rust/"
author: "Simon Willison"
category: Note
tags: [sqlite, sparql, rust, rdf, ferramentas]
ingested: 2026-10-29
---

# sparqlite: SPARQL 1.1 inside SQLite, written in Rust

**Fonte:** Simon Willison | **Data:** 2026-10-16 | **URL:** https://simonwillison.net/2026/Oct/16/sqlite-sparql-rust/

## Resumo

sparqlite: extensão loadable do SQLite escrita em Rust que guarda quads RDF em tabelas comuns e executa queries e updates SPARQL 1.1 nativamente dentro do processo SQLite.

## Ideias principais

- Termos integer-encoded, covering indexes, cost-based planner e joins em batch
- 3,5× de speedup sobre tradução para SQL em certas queries; leitor direto de B-tree do SQLite opcional

## Notas e conexões

- [[slipbox/References]]
