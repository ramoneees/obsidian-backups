---
title: "We just shipped support for the ugliest part of HTTP: Vary"
source: Simon Willison
date: 2026-09-30
url: https://simonwillison.net/2026/Sep/23/hn-49823961/
author: Simon Willison
category: Comentário Hacker News
tags: [http, vary, cloudflare, caching, content-negotiation]
ingested: 2026-10-03
---

# We just shipped support for the ugliest part of HTTP: Vary

**Fonte**: Simon Willison (Simon Willison)
**Data**: 2026-09-30 . **URL**: https://simonwillison.net/2026/Sep/23/hn-49823961/

## Resumo

Comentário de Simon Willison no Hacker News sobre a Cloudflare ter lançado suporte ao header Vary: ele esperava isso "for years". O problema clássico é o content negotiation por header — user agents que enviam "accept: text/html" recebem HTML, os que não enviam recebem JSON — que era impossível de colocar atrás do cache da Cloudflare porque ela ignorava o Vary em tudo que não fossem imagens, arriscando servir JSON cached a quem esperava HTML.

## Ideias principais

- **Workaround pessoal**: independente da novidade da Cloudflare, Simon decidiu nunca usar esse padrão — prefere URLs que devolvem previsivelmente HTML ou JSON, servindo o JSON através de um sufixo `.json` nas suas apps.

## Notas e conexoes

[[slipbox/References]]
