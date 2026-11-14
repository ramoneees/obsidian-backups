---
title: "datasette-leaflet 0.3"
source: Simon Willison
date: 2026-11-13
url: https://simonwillison.net/2026/Nov/13/datasette-leaflet/
category: Release
tags: [datasette, release, plugins, leaflet, openstreetmap]
blogwatcher_id: 1343
type: beat (release announcement)
ingested: 2026-11-14
---

# datasette-leaflet 0.3

## Resumo

Release 0.3 do **datasette-leaflet**, o plugin que embute o Leaflet para que outros plugins do Datasette dependam dele.

O problema: o OpenStreetMap tem uma política razoável de que hits no tile server hospedado enviem header de referrer. As páginas de tabela do Datasette usavam o header HTTP `Referrer-Policy: no-referrer`, o que fazia plugins que carregavam tiles da OSM violarem essa política. O 0.3 passa a definir a política de referrer nos pedidos de tiles como `strict-origin-when-cross-origin` — passa o host, mas não o path completo da página.

## Notas e Conexões

- Conecta com [[Simon Willison-datasette-cluster-map 0.19]] — publicada no mesmo dia, é a release dependente que motivou este fix (tiles da OSM com referrer correto).
- Página do plugin: https://github.com/simonw/datasette-leaflet
- [[slipbox/References]]
