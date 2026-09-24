---
title: "Gemini 3.8 TTS Playground"
source: https://simonwillison.net/2026/Sep/23/gemini-tts-playground/
date: 2026-09-24
tags: [ia, tts, gemini, automacao]
---

O Google lançou dois modelos de texto-para-voz, `gemini-3.8-flash-tts` e `gemini-3.8-flash-lite-tts`, com catálogo de mais de 2.000 vozes. O detalhe provocador: dá para criar voz customizada com apenas 30 segundos de áudio — "sua voz ou uma voz que você tem direitos de usar".

Simon Willison vibe-coded um playground bring-your-own-key em cima da API (que tem CORS aberto): narração de voz única ou conversas multi-personagem, cada fala com voz e estilo de entrega próprios ("excited and gossipy" vs "calm and unimpressed"). As configurações ficam salvas na URL, prontas para compartilhar.

Os números importam: 1min18s de áudio gerado em ~20 segundos, por 2,74 centavos de dólar — no modelo caro, não no Flash-Lite. Voz sintética de qualidade deixou de ser projeto de laboratório e virou linha de planilha de custos.

## Por que importa

- TTS é exatamente o que está desativado no Hermes (auto_tts off desde ago/2026) — a demanda explícita agora custa centavos e roda em segundos, com voz própria a partir de 30s de amostra.
- Multi-speaker com estilos por linha abre porta para audiolivros, devocionais em áudio e protótipos de conteúdo sem estúdio.
- O padrão do Simon (vibe-code de ferramenta fina sobre API com CORS aberto, BYOK) é receita replicável para tools internas.

## Frases notáveis

> "It took ~20 seconds to generate 1m 18s of audio using Gemini 3.8 Flash TTS (not the cheaper Flash-Lite), at a cost of 2.74 cents."

> "...the ability to create a custom voice with 'just a 30-second audio sample of your voice or a voice you have the rights to use'."
