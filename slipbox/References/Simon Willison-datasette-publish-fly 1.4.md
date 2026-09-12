---
title: "datasette-publish-fly 1.4"
source: "Simon Willison"
date: 2026-09-11
url: "https://simonwillison.net/2026/Sep/11/datasette-publish-fly/"
tags: [reference, simon-willison, datasette, fly-io, releases, deploy]
ingested: 2026-09-12
---

# datasette-publish-fly 1.4

**Fonte:** Simon Willison (release note)
**Data:** 11 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/11/datasette-publish-fly/
**Release:** https://github.com/simonw/datasette-publish-fly/releases/tag/1.4

## Resumo

Release do plugin Datasette para publicar dados no Fly.io. Mudanças:

- Define `force_https=true` no `fly.toml` ([#31](https://github.com/simonw/datasette-publish-fly/issues/31))
- Fix para o bug "Volume could not be found" ([#32](https://github.com/simonw/datasette-publish-fly/issues/32))
- Compatível com **deploy tokens com escopo de app** ([#34](https://github.com/simonw/datasette-publish-fly/issues/34))

## Notas e conexões

- Relevante para deploys no Fly: tokens com escopo de app são a prática recomendada (menor privilégio) — o plugin agora segue isso.
- [[slipbox/References]]
