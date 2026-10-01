---
title: "Photo Scrubber — local face blur & metadata removal"
source: "https://simonwillison.net/2026/Sep/29/photo-scrubber/"
date: 2026-10-01
tags: [ia, ferramentas, privacidade, llm-dev]
---

Post curtinho do Simon Willison, mas o que interessa é o padrão de uso. Ele fotografou uns manifestantes, não quis compartilhar fotos de estranhos com rosto identificável, e pediu ao GPT-6 Astra que construísse a ferramenta: Photo Scrubber, que detecta rostos e desfoca automaticamente. Tecnicamente: MediaPipe (C++ do Google) compilado para WebAssembly via tasks-vision, com o modelo de detecção BlazeFace — tudo rodando local no browser, zero upload. Remoção de metadados incluída.

Dois padrões aqui valem mais que a ferramenta em si. Primeiro: "precisei de uma ferramenta pequena de visão computacional, descrevi em linguagem natural, um frontier model gerou, um commit e está no ar" — o fluxo inteiro levou o tempo de uma conversa. Segundo: a escolha de arquitetura orientada a privacidade (inferência local no browser, nada sai do dispositivo) foi feita por padrão, não como custo extra — o que era exótico há dois anos hoje é o caminho rápido.

Código aberto no GitHub dele (simonw/tools), commit único visível — dá para inspecionar exatamente o que o modelo gerou.

## Por que importa

- Caso canônico do teu fluxo delega-tudo-ao-agente: uma ferramenta utilitária nascida de um commit gerado por LLM. É o mesmo padrão sisyphus→review→dogfood que você roda no tekton, em escala de brinquedo.
- Inferência local no browser via WASM é relevante para o precisase (Casa da Cidade): blurring de rostos em fotos de voluntariado/doações antes de publicar seria um recurso de privacidade trivial de embedar, sem backend de visão.
- Ethos alinhado ao teu: ferramenta de privacidade que nem precisa confiar em nuvem — roda local, código aberto, auditável.

## Frases notáveis

> "I took a photograph of some protesters, then thought about how I don't like sharing photographs of strangers with identifiable faces."

> (ferramenta construída com) "Google's MediaPipe C++ library, compiled to WebAssembly … plus the BlazeFace face detection model."
