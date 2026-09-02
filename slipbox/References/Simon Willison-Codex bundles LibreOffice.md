---
source: Simon Willison
title: "Codex bundles LibreOffice"
author: Simon Willison
date: 2026-09-01
url: https://simonwillison.net/2026/Sep/1/codex-libreoffice/
category: ai
tags: [codex, openai, chatgpt, libreoffice, runtimes, disk-usage]
ingested: 2026-09-02
status: summary
---

# Codex bundles LibreOffice

## Fonte

- **Source**: Simon Willison (blog, note)
- **Author**: Simon Willison
- **Published**: 2026-09-01
- **URL**: https://simonwillison.net/2026/Sep/1/codex-libreoffice/

## Resumo

Nota curta. Mexendo no `~/.cache/` com OmniDiskSweeper, Simon achou **1,7 GB** em `codex-primary-runtime` — o app desktop do OpenAI Codex (rebatizado para ChatGPT) embarca:

- Instalação completa de **Python** (~441 MB)
- Instalação completa de **Node.js** (~446 MB)
- Binários nativos de **Poppler** (188 MB), **git** (148 MB)
- **LibreOffice headless** (~430 MB — fork do OpenOffice.org de 2010)

O folder `~/.cache/codex-runtimes/codex-primary-runtime/plugins/openai-primary-runtime/plugins/documents` inclui **skills que ensinam o Codex a encontrar e usar esses binários**.

## Key Takeaways

- Agents de coding estão virando runtimes autocontidos: Python + Node + git + Poppler + LibreOffice empacotados para o agente processar qualquer formato de documento sem depender do sistema do usuário.
- Curioso paralelo arquitetural com a stack Hermes (plugins/skills apontando para binários locais).
- Custo: 1,7 GB escondidos em cache — vale saber o que esses apps depositam no disco.
