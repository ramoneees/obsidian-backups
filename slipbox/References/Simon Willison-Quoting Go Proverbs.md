---
source: "Simon Willison"
title: "Quoting Go Proverbs"
date: 2026-11-17
url: https://simonwillison.net/2026/Nov/17/go-proverbs/
author: "Simon Willison (citação de Go Proverbs, go-proverbs.github.io)"
category: "Quotation"
tags: [reference, quotation, go, programming, dependencias]
blogwatcher_id: 1376
ingested: 2026-11-17
---

# Quoting Go Proverbs

**Fonte:** Simon Willison's Weblog (quotation post)
**Data:** 17 de novembro de 2026
**URL:** https://simonwillison.net/2026/Nov/17/go-proverbs/

## Resumo / notas principais

Citação dos Go Proverbs (coleção de Rob Pike, go-proverbs.github.io):

> "A little copying is better than a little dependency."

Um pouquinho de cópia vale mais do que um pouquinho de dependência — o custo real de uma dependência (manutenção, supply chain, API que muda) quase sempre supera o custo local de duplicar uma função pequena.

## Notas e conexões

- O provérbio descreve na prática a filosofia de engenharia do próprio Willison: no post do mesmo dia sobre o Datasette Lite reescrito ([[Simon Willison-Running the full server-side Datasette Python app in the browser with service workers and Pyodide]]) ele monta demo de bug/reprodução linkando direto URLs do lite.datasette.io em vez de subir servidores — copiar o link em vez de depender de infraestrutura.
- [[slipbox/References]]
