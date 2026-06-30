---
title: "Have your agent record video demos of its work with shot-scraper video"
source: Simon Willison
date: 2026-06-30
url: https://simonwillison.net/2026/Jun/30/shot-scraper-video/
author: Simon Willison
category: Tooling
tags: [shot-scraper, coding-agents, demos, video, playwright, datasette, ai-agents]
ingested: 2026-06-30
---

# Have your agent record video demos of its work with shot-scraper video

## Summary

Novo subcomando `shot-scraper video` (parte do release 1.10) aceita um arquivo `storyboard.yml` que define uma rotina contra um app web, e usa Playwright para gravar um vídeo dessa rotina. Simon argumenta que coding agents precisam produzir **demos** do trabalho deles — esta é sua tentativa mais recente de viabilizar isso.

## Key Ideas

- **The big idea:** agents que escrevem código também precisam provar que ele funciona. Screenshots estáticos não bastam — vídeo da execução real é a evidência.
- **A storyboard YAML** define:
  - `server` (como rodar a app localmente)
  - `url`, `viewport`, `cursor`, `wait_for`, `javascript` (configuração do browser)
  - `scenes` (sequência nomeada de `do:` steps: `pause`, `click`, `wait_for`, `fill`, `wait_for_url`)
- **Exemplo real:** demo de bulk-insert no Datasette — duas cenas, ~20 steps. Construído inteiramente por **GPT-5.5 xhigh** no Codex Desktop, a partir do prompt "Review the changes on this branch."
- **Autenticação:** `--auth` aceita um JSON com cookie (documentado em [authentication docs](https://shot-scraper.datasette.io/en/stable/authentication.html)).
- **Output:** `--mp4` opcional (default parece ser webm). Arquivo vai para o path definido em `output:`.
- **Why this matters:** agents já podem escrever código E tests. Mas "show, don't tell" para humanos exige vídeo. A barreira de "gravar um demo" caiu de horas para minutos.
- **Documentation:** [shot-scraper video docs](https://shot-scraper.datasette.io/en/stable/video.html) com exemplos mais simples.

## Aplicação Prática

- Se você constrói features com coding agents, adicione um step final no prompt: "also create a shot-scraper video demo of the new feature."
- Para demos internos / PRs: storyboard YAML é versionável no repo junto com o código.
- Útil para o [obsidian-backups] — poderia gravar demos de fluxos complexos (sync, ingest, etc.).

## Notas e Conexões

- [[Simon Willison-shot-scraper 1.10]] — release notes deste mesmo dia
- [[Coding agents]] (a criar) — práticas de uso de coding agents
- [[Datasette]] (a criar) — projeto subjacente
- [[Playwright]] (a criar) — base do shot-scraper
- [[Showboat-and-Rodney]] (referência interna do Simon) — ferramentas similares para demos
