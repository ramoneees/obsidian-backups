---
title: "Using Blender with coding agents on macOS"
source: "Simon Willison"
date: 2026-09-05
url: "https://simonwillison.net/2026/Sep/5/blender-coding-agents-macos/"
tags: [reference, ai, blender, coding-agents, llms]
ingested: 2026-09-05
---

# Using Blender with coding agents on macOS

**Fonte:** Simon Willison's Weblog
**Data:** 5 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/5/blender-coding-agents-macos/

## Resumo

TIL curto: modelos frontier recentes ficaram *muito bons* usando Blender via coding agents. Dá para gerar arquivos `.blend` editáveis, renderizar imagens e até filmes (sequência de frames + `ffmpeg`). Simon testou com ChatGPT Codex (GPT-6 Astra) no Mac.

## Notas principais

- **Setup mínimo:** instalar o app completo do Mac via blender.org e apontar o agente para ele — nada de plugin especial.
- **Prompt inicial usado:** `Use the already install /Applications/Blender to render a scene of a pelican riding a bicycle`.
- **Refinamento iterativo:** dois follow-ups simples — `OK add a background and a lot of flair` e `OK make it a whole lot better` — produziram a imagem final (pelicano de bicicleta num calçadão à beira-mar ao pôr do sol, com chapéu, cachecol, balões e barracas de praia).
- **Mecanismo:** o agente escreve scripts usando a Python API do Blender ([código final no GitHub](https://github.com/simonw/gpt-6-astra-blender-pelican-bicycle/blob/main/work/pelican_final.py)) e renderiza via CLI.
- **Extensão possível:** renderizar sequência de imagens e combinar com `ffmpeg` para gerar animações/filmes.
- Tags do post: ai, generative-ai, llms, blender, pelican-riding-a-bicycle, coding-agents, gpt-6-astra.

## Conexões

- Continuação do teste de pelicanos: [[resumo-Astra-Pelican-Comparison-Grid-SimonWillison]] (grid comparativo do Astra, 4/set).
- Tópicos: [[LLM]], [[OpenAI]], [[Coding Agents]], [[Simon Willison]].
- Ideia prática: o mesmo padrão (agente + app local com Python API/CLI) pode valer para outras ferramentas desktop no Mac.
