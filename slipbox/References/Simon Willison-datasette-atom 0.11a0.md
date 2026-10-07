---
title: "datasette-atom 0.11a0"
source: Simon Willison
date: 2026-10-06
url: https://simonwillison.net/2026/Oct/6/datasette-atom/
author: Simon Willison
category: release
tags: [datasette, atom, plugins, releases]
ingested: 2026-10-07
---

# datasette-atom 0.11a0

**Fonte**: Simon Willison (release)
**Data**: 2026-10-06 . **URL**: https://simonwillison.net/2026/Oct/6/datasette-atom/

> Plugin Datasette que adiciona formato de saída `.atom` — fix de compatibilidade com os alphas mais recentes.

## Resumo

Release menor: compatibilidade com os alphas atuais do Datasette, o que permitiu subir o site datasette.io para o Datasette 1.0a41.

## Ideias principais

- Manutenção silenciosa de ecossistema: cada alpha do core quebra plugins, e cada fix de plugin destrava o upgrade dos sites de produção.
- Atom feeds como cidadão de primeira classe em ferramenta de dados — saída sindicável de queries SQL segue útil em 2026.

## Notas e conexoes

- O alpha que motivou o fix trouxe o OpenTelemetry: [[Simon Willison-Using Parseable with Datasette for OpenTelemetry traces]].
- [[slipbox/References]]
