---
title: "Gemini Live audio"
source: https://simonwillison.net/2026/Sep/15/gemini-live/
date: 2026-09-16
tags: [ia, llm, websockets, tools]
---

# Gemini Live audio

## Resumo

O Google lançou o **Gemini 3.8 Live** e o **3.8 Live Extended Thinking**, dois modelos speech-to-speech que seguem o formato da família GPT-Live da OpenAI. Simon Willison, com sua marca registrada de "construir em público", apontou o GPT-6 Astra Extra High para a documentação e teve de volta uma web UI completa para conversar por voz com os novos modelos — tudo num único arquivo HTML, sem bibliotecas.

A implementação é notavelmente enxuta: conecta ao endpoint WebSocket `wss://generativelanguage.googleapis.com/...BidiGenerateContent` e usa a Web Audio API (`AudioContext`) tanto para captura quanto para playback do áudio. A interface permite selecionar modelo e voz, definir system prompt, e — o detalhe que importa — **interromper o modelo enquanto fala**, com transcrição em tempo real e download do transcript.

O ponto interessante para quem constrói: a barreira de entrada para interfaces de voz com LLM despencou. O que há um ano exigiria stack de áudio dedicado hoje é um WebSocket + Web Audio API num arquivo só. O padrão speech-to-speech nativo (sem pipeline ASR→LLM→TTS) está se consolidando como commodity.

Willison publica tanto a ferramenta quanto o gist do código — o ciclo "docs → agente → UI funcional em horas" é em si o maior sinal do estado da arte.

## Por que importa

- **Automação/agentes**: interação por voz com LLMs virou infraestrutura de baixo custo — relevante para qualquer ideia de agente hands-free (lembra o interesse em voz pt-BR já configurada no setup).
- **Arquitetura minimalista**: zero bibliotecas, só WebSocket + Web Audio API. Padrão de simplicidade que conversa com a filosofia de "reset-over-patch" e ferramentas pequenas.
- **Speech-to-speech nativo** substituindo pipelines ASR/LLM/TTS é a mesma curva que tornou agentes de código commodity — vale acompanhar para não construir sobre stack que morre.

## Frases notáveis

> "I pointed GPT-6 Astra Extra High at the documentation and had it build me this web UI for trying out the new models."

> "The implementation uses no libraries. It connects to the wss://... WebSocket endpoint and uses a Web Audio API AudioContext for both capture and playback."
