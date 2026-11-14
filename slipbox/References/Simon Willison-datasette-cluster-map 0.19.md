---
title: "datasette-cluster-map 0.19"
source: Simon Willison
date: 2026-11-13
url: https://simonwillison.net/2026/Nov/13/datasette-cluster-map/
category: Release
tags: [datasette, release, plugins, geospatial, openstreetmap]
blogwatcher_id: 1342
type: beat (release announcement)
ingested: 2026-11-14
---

# datasette-cluster-map 0.19

## Resumo

Release 0.19 do **datasette-cluster-map**, um dos plugins mais antigos do Datasette e "ainda um dos favoritos" do Simon. Agora compatível com o Datasette 1.0a42 e dependente do novo **datasette-leaflet** para garantir que os tiles do OpenStreetMap sejam pedidos com header de referrer (política atual da OSM para o tile server hospedado).

A demonstração do post: mapa das usinas de energia da PG&E (Califórnia), que também exibe as facets recentemente redesenhadas do Datasette.

## Notas e Conexões

- Conecta com [[Simon Willison-datasette-leaflet 0.3]] — a nova dependência desta release, publicada no mesmo dia (13/11); é ela que resolve a política de referrer da OSM.
- Contexto da série Datasette 1.0 no vault: [[Simon Willison-datasette 1.0a41]] — a compatibilidade aqui é com o 1.0a42, alpha seguinte ainda sem nota.
- Página do plugin: https://github.com/simonw/datasette-cluster-map
- [[slipbox/References]]
