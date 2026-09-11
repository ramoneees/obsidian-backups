---
title: "Don't sleep on wrapture"
source: "Simon Willison"
date: 2026-09-11
url: "https://simonwillison.net/2026/Sep/11/wrapture/"
tags: [reference, simon-willison, python, testing, observabilidade, monkey-patching, open-source]
ingested: 2026-09-11
---

# Don't sleep on wrapture

**Fonte:** Simon Willison (nota)
**Data:** 11 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/11/wrapture/

## Resumo

Simon chama atenção para o **wrapture**, novo pacote de monkey patching de Graham Dumpleton (criador do mod_wsgi), que ele considera "eminemente indispensável" e com buzz curiosamente baixo. A ideia forte: **uma única lib que serve testing E observabilidade** (tracing estilo New Relic) ao mesmo tempo. Ainda é alpha, mas muito usável.

## O que ela faz (pelos ~10 tutoriais já publicados)

- **Substitui unittest.mock** para casos comuns de patching em testes.
- **Recording de chamadas** como timelines, exibidas em árvore.
- **Phased behaviour**: método altera comportamento entre chamadas consecutivas.
- **Além de callables**: atributos, dicionários, generators.
- **Live tracing** de aplicação em execução.
- **Zero-code tracing**: configuração via arquivo TOML separado, sem tocar no código Python.
- **wrapture-instrumentation** (pacote irmão): instrumentação pronta para flask, django, fastapi, aiohttp, httpx, requests, sqlalchemy, sqlite3, jinja2, grpc, uvicorn, werkzeug etc.
- **Achado de código lento**: timing individual e agregado.
- **Export para OpenTelemetry**.
- Workshops interativos em notebooks JupyterLab.

## Notas e conexões

- Avaliação do Simon: "canivete suíço que, uma vez dominado, dá valor contra todo tipo de problema por anos".
- Candidato natural para debugging/observabilidade de pipelines Python sem alterar código.
- [[slipbox/References]]
