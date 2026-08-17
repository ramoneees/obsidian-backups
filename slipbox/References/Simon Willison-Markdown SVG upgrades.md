---
title: "Markdown SVG upgrades"
source: "Simon Willison"
date: 2026-08-16
url: "https://simonwillison.net/2026/Aug/16/markdown-svg-upgrades/"
tags: [reference, svg, markdown, tools, ffmpeg-wasm]
ingested: 2026-08-17
---

# Markdown SVG upgrades

**Fonte:** Simon Willison
**Data:** 16 de agosto de 2026
**URL original:** https://simonwillison.net/2026/Aug/16/markdown-svg-upgrades/

## Resumo

Atualização da ferramenta [markdown-svg-renderer](https://tools.simonwillison.net/markdown-svg-renderer) (criada em maio, agora com features que merecem post). É a ferramenta ideal dele para compartilhar transcripts Markdown que incluem documentos SVG — problema recorrente dado o hábito de pedir a LLMs desenhos de "pelicans riding bicycles".

Funcionamento: cole Markdown direto no browser, ou aponte para uma URL CORS-friendly / GitHub Gist — a opção URL gera página bookmarkable. Blocos de código SVG viram SVG renderizado + abas.

## Notas principais

- **Abas PNG/JPEG:** renderizam o SVG no browser para esses formatos, com copy/download — útil para plataformas que não aceitam SVG.
- **Aba MP4 (nova do dia):** detecta animações no SVG, estima a duração do loop, renderiza os frames e carrega 30+ MB de ffmpeg.wasm para compilar o vídeo **inteiramente no browser** — SVG animado → MP4 compartilhável.
- Persistência local das conversões; tudo client-side.
- Post é "note" de ferramenta própria — referência prática para quem trabalha com saídas SVG de LLM.

## Conexões

- Ferramenta: https://tools.simonwillison.net/markdown-svg-renderer
- Tópicos: [[SVG]], [[markdown]], [[ffmpeg.wasm]], [[client-side tools]].
- Companheira da mesma semana: [[Simon Willison-CORS Chat]] (mesmo ecossistema de teste de modelos locais).
