---
title: "Creepy crawlies"
source: "Simon Willison"
date: 2026-09-07
url: "https://simonwillison.net/2026/Sep/7/creepy-crawlies/"
category: Link
tags: [reference, crawling, ai-ethics, git, linux, datasette, infraestrutura]
ingested: 2026-09-08
---

# Creepy crawlies

**Fonte:** Simon Willison's Weblog (link post)
**Data:** 7 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/7/creepy-crawlies/

## Resumo / notas principais

Link para [Creepy crawlies](https://people.kernel.org/monsieuricon/creepy-crawlies) de Konstantin Ryabitsev (via HN), sobre a "radiação de fundo" de crawlers abusivos do ponto de vista do git.kernel.org — o repositório Git oficial do kernel Linux:

> TL;DR: gastamos mais ciclos de CPU renderizando commits para scrapers do que em todo o resto do acesso legítimo, incluindo git clones. A qualquer momento, em 5 nós geo-distribuídos, 14 cores fazem nada além de renderizar commits como HTML.

Willison adiciona a preocupação própria: o Datasette serve um número enorme de páginas rastreáveis — o mesmo problema bate em quem publica dados abertos na web.

## Notas e conexões

- Mesma família de [[Stratechery-Write Things Down]]: infraestrutura consumida por agentes/scrapers sem que os humanos percebam.
- [[slipbox/References]]
