---
title: "datasette-maplibre 0.1a0"
source: "Simon Willison"
date: 2026-11-15
url: "https://simonwillison.net/2026/Nov/15/datasette-maplibre/"
tags: [reference, datasette, release, geospatial, mapas, generative-ai, simon-willison]
blogwatcher_id: 1359
ingested: 2026-11-16
---

# datasette-maplibre 0.1a0

**Fonte:** Simon Willison (série de releases)
**Data:** 15 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/15/datasette-maplibre/

## Resumo

Primeiro plugin geoespacial novo do Datasette em bastante tempo: combina a biblioteca MapLibre GL com o OpenFreeMap, servidor gratuito de mapas vetoriais operado por Zsolt Ero. A maior parte foi construída com **um único prompt** ao Claude Fable 5.2, pedindo que olhasse os plugins datasette-cluster-map e datasette-leaflet-geojson e criasse um novo com maplibreGL + openfreemap — "be creative and think outside the box".

## Ideias principais

- **Prompt criativo funcionou:** "think outside the box" rendeu ideias que o autor não pediu — o favorito dele: exibir previews SVG das formas GeoJSON e só carregar o preview WebGL quando a forma entra na viewport (lazy loading de mapa).
- **OpenFreeMap** como backend vetorial gratuito, sem chave de API — alternativa leve ao stack de tiles tradicionais.
- **Demo completa** construída pelo Claude também, rodando no Datasette Lite (Pyodide + WebAssembly, tudo no browser).

## Notas e conexões

- Substituto moderno do par [[Simon Willison-datasette-cluster-map 0.19]] + [[Simon Willison-datasette-leaflet 0.3]] — a era pós-Leaflet do Datasette.
- Lançado no mesmo dia do [[Simon Willison-datasette 1.0a43]] — o plugin já mira o trilho 1.0 alpha.
- [[slipbox/References]]
