---
title: "datasette-arrows 0.1a0"
source: "Simon Willison"
date: 2026-11-18
url: https://simonwillison.net/2026/Nov/18/datasette-arrows/
author: "Simon Willison"
category: "Release"
tags: [reference, datasette, apache-arrow, streaming, plugin, release, simon-willison]
ingested: 2026-11-19
blogwatcher_id: 1403
---

# datasette-arrows 0.1a0

**Fonte:** Simon Willison (release)
**Data:** 18 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/18/datasette-arrows/

## Resumo

Primeiro alpha do plugin `datasette-arrows`, que adiciona exportação streaming no formato Apache Arrow ao Datasette. O contexto é o Datasette 1.0a43, que abriu a porta para plugins implementarem formatos de exportação em streaming via `register_output_renderer()` — o core já faz isso com CSV e TSV (exporta milhões de linhas sem carregar tudo em memória), e o plugin estende o mesmo padrão para Arrow.

## Notas principais

- Regra de ouro do Simon: **nunca lançar um recurso de plugin sem acompanhar de um plugin que o use** — datasette-arrows é a prova de conceito do hook renovado.
- Claude Fable 5.2 sugeriu Apache Arrow como formato ideal de streaming e construiu o plugin "almost in a single shot" — datapoint de agentes codando com supervisão mínima.
- Instalação: `datasette install datasette-arrows` — a caixa de diálogo de export ganha a opção Arrow.
- Na main branch, formatos streaming ainda não aparecem agrupados com CSV/TSV na seção "All rows in this table"; o agrupamento vem no próximo alpha.

## Notas e conexões

- Linha Datasette 1.0 alpha: [[Simon Willison-Running the full server-side Datasette Python app in the browser with service workers and Pyodide]] (o app server-side completo rodando no browser).
- [[slipbox/References]]
