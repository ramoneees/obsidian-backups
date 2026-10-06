---
title: "Scrimshaw Jukebox"
source: Simon Willison
date: 2026-10-06
url: https://simonwillison.net/2026/Oct/6/scrimshaw-jukebox/
author: Simon Willison
category: Tool
tags: [ia, claude, vibe-coding, musica, capacidade-emergente]
ingested: 2026-10-06
---

# Scrimshaw Jukebox

**Fonte**: Simon Willison
**Data**: 2026-10-06 . **URL**: https://simonwillison.net/2026/Oct/6/scrimshaw-jukebox/

> "I am looking for music of the quality of the original secret of Monkey Island"

## Resumo

Willison quis saber se o Claude Opus 5.5 compõe música. O prompt: criar uma barra de jukebox de música de videogame — primeiro desenhar um formato textual simples para notação musical e construir um artifact que a toque em áudio, com faixas de exemplo, na qualidade da trilha do Monkey Island original. Resultado: "surpreendentemente bom", com o aviso de que a saída pendeu muito mais para o tema de Monkey Island do que ele pretendia.

A provocação fica na hipótese: será que compor música competente é como a coisa dos gráficos 3D — uma capacidade nova de modelos de texto que emergiu nos últimos meses? Confirmar exigiria experimentos cuidadosos com modelos recentes e antigos, e ele não fez ainda.

## Ideias principais

- **Formato textual + artifact tocável** é o padrão clássico de Willison para testar capacidade: primeiro dar ao modelo uma representação estruturada que ele mesmo inventa, depois um player que executa. O teste mede modelagem musical de verdade, não regurgitação de áudio.
- **Composição como fronteira emergente**: se a hipótese se confirmar, música competente entra na lista de capacidades que aparecem de repente entre gerações (como o salto de 3D em artifacts) — sem anúncio de feature.
- Prompt de teste replicável em qualquer modelo: barato de rodar e difícil de falsificar (o áudio toca ou não toca).

## Notas e conexoes

- Mesmo método, outro domínio: [[Simon Willison-pwasm 0.2a0]] (o motor WASM vibe-coded) — os dois posts tratam de sondar o que os modelos atuais conseguem de verdade, com artefatos verificáveis como juiz.
- Experimento de 15 minutos para reproduzir no Opus/GLM da casa: vale como teste de regressão divertido a cada troca de modelo.
- [[slipbox/References]]
