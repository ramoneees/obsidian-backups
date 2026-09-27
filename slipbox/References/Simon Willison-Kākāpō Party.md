---
title: "Kākāpō Party"
source: Simon Willison
date: 2026-09-26
url: https://simonwillison.net/2026/Sep/26/kakapo-party/
author: Simon Willison
category: Tool / beat
tags: [claude, pixel-art, playwright, apresentacoes, llms, video-gerado]
ingested: 2026-09-27
---

# Kākāpō Party

**Fonte**: Simon Willison's Weblog (post tipo "Tool"/beat)
**Data**: 2026-09-26 · **URL**: https://simonwillison.net/2026/Sep/26/kakapo-party/

## Resumo

Willison fechou o keynote do WeAreDevelopers World Congress North America com um "STAR moment" celebrando a temporada de reprodução recorde dos kākāpō em 2026 (população em marco histórico, NZ DOC). Pipeline em duas etapas:

1. **Arte**: três fotos de kākāpō do Google Images + um prompt informal para o Claude ("I need you to make an animation in animated pixel art on HTML 5 canvas of obviously pixel art kakapo jumping up and down having a party with confetti... there should be at least 20 of them") → página animada em https://tools.simonwillison.net/kakapo-party. Ele nota o buzz de que Claude Opus 5.5 está particularmente bom em pixel art animada.
2. **Vídeo para o Keynote**: baixou o HTML e pediu a uma sessão local do Claude Code: "Make me a video of file:///.../kakapo-party.html - load it in a browser and click on it a few times to get the confetti effect, 15s, don't start clicking until 3s in, spread clicks around the clickable area". Claude Code escreveu um script Playwright ~40 linhas (viewport 1280x720, record_video_dir, 10 cliques timados em cantos/centro) e produziu exatamente o vídeo do slide final.

## Ideias principais

- **Browser como engine de render para vídeo**: canvas HTML animado + Playwright screencasting = motion graphics gerados por LLM sem After Effects, controlados por cliques timados. Prompt de direção temporal ("não clique antes de 3s", "espalhe cliques") funcionou.
- Padrão reutilizável: *gerar arte interativa no browser → gravar interação como vídeo → embutir em slide*. Serve para demos de qualquer app web.
- O script Playwright é notavelmente curto — dependency header inline (`# /// script / dependencies = ["playwright"]`), clicks listados como tuplas (t, x, y), sleep relativo ao t0.
- Continuação da saga kākāpō no blog de Simon (tags kakapo: 13 posts) — depois de [[Simon Willison-Quoting Andrew Digby]] (agosto), agora a festa.

## Notas e conexões

- Mesma técnica "LLM escreve HTML/canvas animado" de [[Simon Willison-Claude Fable 5.1 made me a really nice animated pelican]] — agora com o passo extra de captura em vídeo.
- Playwright + direção temporal é direto aplicável a QA/vídeos de produto (nossa stack Maestro roda browser too): ponte com [[Tim Challies-Works & Wonders (September 27)]] que citou recriação de apps via Claude.
- Candidate a demo interna: "gere animação pixel art do nosso mascote, clique e filme" em <10 min.
- [[slipbox/References]]
