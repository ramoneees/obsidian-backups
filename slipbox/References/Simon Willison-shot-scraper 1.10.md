---
title: "shot-scraper 1.10"
source: Simon Willison
date: 2026-06-30
url: https://simonwillison.net/2026/Jun/30/shot-scraper/
author: Simon Willison
category: Release
tags: [shot-scraper, release, video, datasette, playwright]
ingested: 2026-06-30
---

# shot-scraper 1.10

## Summary

Release notes curtos: shot-scraper 1.10 introduz o subcomando `shot-scraper video storyboard.yml`, descrito em detalhe no post companion.

## Key Ideas

- **shot-scraper** — CLI utility for taking screenshots of websites, recording video demos and scraping sites using JavaScript.
- **The big new feature:** `shot-scraper video storyboard.yml` — aceita um arquivo YAML que define uma rotina contra um web app e usa Playwright para gravar vídeo.
- **Detalhe completo:** ver [[Simon Willison-Have your agent record video demos of its work with shot-scraper video]].
- **Link de release:** https://github.com/simonw/shot-scraper/releases/tag/1.10

## Aplicação Prática

- Atualizar shot-scraper se você já usa: `pip install -U shot-scraper` ou `uv tool upgrade shot-scraper`.
- Testar com o storyboard do post companion.

## Notas e Conexões

- [[Simon Willison-Have your agent record video demos of its work with shot-scraper video]] — post companion com detalhes e exemplo
- [[shot-scraper]] (a criar) — nota mãe da ferramenta
- [[Datasette]] (a criar) — ecossistema
- [[Playwright]] (a criar) — engine subjacente
