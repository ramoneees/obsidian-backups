---
title: "A shot-scraper-style JSON API on Bun 1.4's new Bun.WebView"
source: "Simon Willison"
date: 2026-08-20
url: "https://simonwillison.net/2026/Aug/20/bun-webview-json-api/"
tags: [reference, research, bun, browsers, webview, screenshot]
ingested: 2026-08-21
---

# A shot-scraper-style JSON API on Bun 1.4's new Bun.WebView

**Fonte:** Simon Willison (research note)
**Data:** 20 de agosto de 2026
**URL original:** https://simonwillison.net/2026/Aug/20/bun-webview-json-api/ (repo: github.com/simonw/research/tree/main/bun-webview-json-api)

## Resumo

Bun 1.4 saiu (primeira versão estável desde a reescrita em Rust) e Simon testa o novo `Bun.WebView` — automação de browser first-class no core do Bun via WebKit do macOS ou Chromium local por CDP. Protótipo vibe-codado (Claude Code para web): serviço JSON estilo shot-scraper para avaliar JavaScript e tirar screenshots sem Puppeteer/Playwright.

## Notas principais

- **Bun 1.4:** reescrita Zig→Rust (downtplayed nas release notes), +2.900 bugs fixados, -5x CPU idle, -35% memória, +50% startup no Linux; novos `Bun.Image`, `Bun.WebView`, `Bun.markdown`, `Bun.cron()`, `Bun.Terminal`, `bun run/test --parallel`, `bun audit fix`, `bun dedupe`, `bun prune`.
- **Protótipo:** ~150 linhas de TypeScript, zero dependências; endpoints `/javascript`, `/screenshot`, `/healthz`; uma tab de browser por request (concorrente), resultados e erros como JSON.
- Motivação secundária: medir RAM de um serviço assim — **~192–256 MB** de container para rodar um Chrome completo contra páginas complexas (testado via cgroups).
- Padrão recorrente no Simon: prototype com Claude Code para responder pergunta de viabilidade/custo.

## Conexões

- Tópicos: [[Bun]], [[browser automation]], [[CDP]], [[screenshot]], [[prototipagem com IA]].
- Dialoga com [[Simon Willison-Stop Making TUIs]] (agents barateando tools) e com [[resumo-smolmachines-sandbox-simon-willison]].
