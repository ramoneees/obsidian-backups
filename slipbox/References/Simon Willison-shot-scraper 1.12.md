---
title: "shot-scraper 1.12"
source: Simon Willison
date: 2026-09-13
url: https://simonwillison.net/2026/Sep/13/shot-scraper/
author: Simon Willison
category: Release
tags: [shot-scraper, release, webp, playwright, screenshots]
ingested: 2026-09-14
---

# shot-scraper 1.12

## Resumo

Release notes curtos: shot-scraper 1.12 adiciona **suporte a WebP** para screenshots.

```bash
shot-scraper https://simonwillison.net -o screenshot.webp --quality 80
```

## Key ideas

- `--quality N` define a qualidade; **sem a flag, o WebP é lossless**.
- Na experiência do Simon, screenshots WebP são quase sempre **significativamente menores** que JPEG/PNG equivalentes (exemplos no PR #210).
- Motivação: gerar o screenshot do novo tool commit-rewriter.

## Aplicação prática

- `uv tool upgrade shot-scraper` / `pip install -U shot-scraper` se já usa; trocar PNG por WebP + `--quality 80` em pipelines de screenshots.

## Notas e conexões

- [[Simon Willison-shot-scraper 1.10]] — release anterior (shot-scraper video)
- [[Simon Willison-Have your agent record video demos of its work with shot-scraper video]] — post companion do 1.10
- [[resumo-commit-rewriter-0-1]] — tool que motivou o WebP
- [[slipbox/References]]
