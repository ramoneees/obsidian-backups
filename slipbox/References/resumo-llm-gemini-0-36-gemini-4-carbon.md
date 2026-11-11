---
title: "llm-gemini 0.36"
source: https://simonwillison.net/2026/Nov/10/llm-gemini/
date: 2026-11-11
tags: [ia, llm-release, gemini, custo-modelos]
---

Release notes do plugin llm-gemini 0.36 do Simon Willison, na prática um aviso de dois fatos: o Gemini 4 Carbon saiu do acesso restrito ("subset of cyber defenders") e está disponível para todo mundo via plugin, e a janela de preço promocional vai fechar em 1º de dezembro.

O Carbon é o melhor Gemini já lançado, com preço de lançamento de $2/milhão de tokens de entrada e $10 de saída — mesmo patamar de GPT-6.1 Sol e Claude Sonnet 5.5 — mas com duplicação agendada para 1/12 ($4/$20), aí igualando o Claude Opus 5.5. Ou seja: quem quiser rodar benchmarks ou cargas reais no modelo top da Google, a conta dobra em três semanas. O plugin também expõe os três níveis de esforço de raciocínio (low/medium/high, default medium).

A parte demonstrativa é a de sempre no blog do Simon: pelicans nos três níveis de thinking, mais um teste no Antigravity IDE da Google — animação Three.js de um mech em Manhattan usando dados do OpenStreetMap. O update mostra o resultado mais pesado: com o /swarm do Antigravity, o Carbon coordenou subagentes para construir um jogo 3D de mundo aberto (modelagem de assets no Blender via referências de Omni e Nano Banana, shaders WebGL, áudio procedural + música Lyria).

## Por que importa
- Decisão de custo com prazo: preço do Google top de linha dobra em 1º de dezembro — relevante para o roteamento do LiteLLM (litellm.ramoneees.com) e para escolher quando valer a pena esbarrar no Gemini.
- O padrão de mercado se confirma: modelo top da Google custando o mesmo que Opus 5.5 — o piso de preço da fronteira subiu, e vale registrar para as escolhas de modelo dos fluxos (pesado→GLM, visão→flash).
- /swarm coordenando subagentes (Blender, shaders, áudio) é mais um datapoint da tendência que já aparece no post do IPO da Anthropic: orquestração multi-agente fazendo trabalho criativo-técnico ponta a ponta.

## Frases notáveis
> "Priced at $2/million input and $10/million output at launch (that's GPT-6.1 Sol / Claude Sonnet 5.5 prices) but scheduled to double in price to $4/$20 on December 1st (same as Opus 5.5)."

> "Using Google Antigravity's /swarm feature, Carbon built an open-world 3D game where you explore Google's Mountain View campus as a pelican riding a GBike — coordinating subagents to model 3D assets in Blender."
