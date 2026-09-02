---
source: Simon Willison
title: "Tool: GeoJSON Map Viewer"
author: Simon Willison
date: 2026-09-01
url: https://simonwillison.net/2026/Sep/1/geojson/
category: tools
tags: [geojson, maps, openstreetmap, tools, chatgpt, leaflet]
ingested: 2026-09-02
status: summary
---

# Tool: GeoJSON Map Viewer

## Fonte

- **Source**: Simon Willison (blog, tool)
- **Author**: Simon Willison
- **Published**: 2026-09-01
- **URL**: https://simonwillison.net/2026/Sep/1/geojson/
- **Tool**: https://tools.simonwillison.net/geojson

## Resumo

Nova ferramenta: **visualizar GeoJSON num mapa OpenStreetMap interativo** com estilo customizável — colar Feature/FeatureCollection/Geometry no editor, ajustar cor e opacidade do preenchimento, renderizar no mapa e exportar PNG. Dados ficam no browser.

Origem: ajudando Natalie a reunir mapas de limites políticos locais na Califórnia (Granada Community Services District e Midcoast Community Council). Pediu sugestões de ferramentas ao GPT-5.6-Sol — **que construiu uma proativamente**. Iterações com Claude Code (web) e Fable 5.1 até o resultado final.

## Key Takeaways

- ChatGPT Work extrai e combina ficheiros de fontes de dados governamentais e monta exatamente o polígono pedido ("I want a polygon that represents the exact boundary of the El Granada GCSD").
- Fluxo moderno de building de tools: pedir sugestão → o modelo constrói → iterar com agentes de coding → publicar. Ferramenta individual levada a done em horas.
- Múltiplas shapes com cores/opacidade próprias, URL-parametrizável para compartilhar visualizações.
