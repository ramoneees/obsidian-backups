---
title: "datasette-llm 0.1a9"
source: Simon Willison
date: 2026-10-31
url: https://simonwillison.net/2026/Oct/31/datasette-llm/
author: Simon Willison
category: Release
tags: [llm, datasette, sqlite, release, tools]
ingested: 2026-11-01
---

# datasette-llm 0.1a9

**Fonte:** Simon Willison
**Data:** 31 de outubro de 2026
**URL:** https://simonwillison.net/2026/Oct/31/datasette-llm/

## Resumo

Release pontual do plugin `datasette-llm` — a camada de integração LLM que outros plugins do Datasette podem depender. A mudança: o plugin agora herda o modelo padrão já configurado no CLI `llm`, eliminando a necessidade de passar explicitamente um modelo ao usar o Datasette Agent. Simon sinaliza que melhorias maiores no Datasette Agent estão a caminho.

## Ideias principais

- Antes era preciso rodar com `-s plugins.datasette-agent.default_model gpt-6-astra` para definir o modelo; agora o default do `llm` é detectado automaticamente.
- Comando simplificado de uso: `uvx --with datasette-agent datasette content.db --internal internal.db`.
- Padrão de design interessante: um plugin "base" (datasette-llm) que centraliza a configuração de modelo para que plugins de nível superior (datasette-agent) não dupliquem configuração.

## Notas e conexões

- Exemplo do benefício de tratar configuração de LLM como infraestrutura compartilhada em vez de flag por ferramenta — mesma lógica de "qual modelo usar" discutida em [[Simon Willison-An opinionated guide to which AI to use to do stuff]].
- Ferramentas SQLite-as-plataforma: parente direto do espírito de [[Simon Willison-sparqlite: SPARQL 1.1 inside SQLite, written in Rust]].
- [[slipbox/References]]
