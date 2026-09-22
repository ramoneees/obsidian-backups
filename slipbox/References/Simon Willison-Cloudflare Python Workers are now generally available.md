---
source: "Simon Willison"
title: "Cloudflare Python Workers are now generally available"
date: 2026-09-21
url: https://simonwillison.net/2026/Sep/21/cloudflare-python-worker/
author: "Simon Willison"
category: "Link post"
tags: [python, cloudflare, webassembly, pyodide, serverless, infra]
ingested: 2026-09-22
---

# Cloudflare Python Workers are now generally available

**Fonte:** Simon Willison (weblog, link post sobre o anúncio da Cloudflare)
**Data:** 21 de setembro de 2026
**URL:** https://simonwillison.net/2026/Sep/21/cloudflare-python-worker/

## Resumo

Depois de dois anos em preview, o suporte a Python nos Workers server-side da Cloudflare está estável: "Python is now a first-class, fully supported language on the Cloudflare Developer Platform". O mecanismo: Python compilado para WebAssembly via Pyodide, rodando dentro do runtime workererd baseado em V8.

## Ideias principais

- **Limitações documentadas:** `multiprocessing` e `threading` são não-funcionais na VM WebAssembly — o modelo de execução é o de isolates, não de processo completo.
- **Dev local sério:** a tool `pywrangler` (publicada no PyPI como `workers-py`) roda uma simulação local completa da stack — código executado com Pyodide em WebAssembly em V8, dentro de um binário `workerd` de ~123MB. Paridade dev/prod de verdade, não emulação rasa.
- **Investimento no ecossistema:** o anúncio é creditado a Gyeongjae Choi, Dominik Picheta e Hood Chatham — Choi e Chatham são mantenedores core do Pyodide. A Cloudflare está comprando o Python edge com gente de dentro do ecossistema, não de fora.

## Notas e conexões

- Alternativa serverless a considerar para webhooks/rotas de APIs do stack (hoje resolvido com Fly.io/n8n): custo de cold-start baixo por isolate, mas sem threads.
- Pyodide/WebAssembly como ponte "Python em qualquer runtime V8" ecoa o Datasette-into-lite-python do próprio Willison — o ecossistema Pyodide está virando infraestrutura, não curiosidade.
- [[slipbox/References]]
