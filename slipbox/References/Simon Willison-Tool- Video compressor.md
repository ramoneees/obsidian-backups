---
title: "Tool: Video compressor"
source: "Simon Willison"
date: 2026-09-07
url: "https://simonwillison.net/2026/Sep/7/video-compressor/"
category: Tool
tags: [reference, ffmpeg, video, webassembly, claude-code, vibe-coding, ferramenta]
ingested: 2026-09-08
---

# Tool: Video compressor

**Fonte:** Simon Willison's Weblog (tool post)
**Data:** 7 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/7/video-compressor/

## Resumo / notas principais

Ferramenta publicada: [tools.simonwillison.net/video-compressor](https://tools.simonwillison.net/video-compressor) — comprime vídeos no navegador com o build WebAssembly do FFMPEG (nada sai da máquina).

Origem em uma frase que resume vibe-coding em 2026: gravou um demo da animação de Equal Earth no telefone, quis publicar versão otimizada, e pediu ao **Claude Fable 5.1 no Claude Code para web** que construísse a ferramenta.

Especificações visíveis: cinco presets (Largest→Smallest) variando resolução (854×370 / 640×276), CRF 22–28, áudio 128–64 kbps; opções de encoder speed, perfil H.264, limite 30 fps, strip de metadata, drop de áudio e "primeiros 10 s apenas". Resultado do exemplo: 5 versões em 11,8 s; a menor com 145 KB (48% do original), cada uma com o comando ffmpeg equivalente visível.

## Notas e conexões

- Irmã de [[Simon Willison-Tool- Mercator ↔ Equal Earth]] — mesma tarde, mesmo fluxo (agente constrói ferramenta de uso único).
- [[slipbox/References]]
