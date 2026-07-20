---
source: Simon Willison
title: "Who's Afraid of Chinese Models?"
author: Simon Willison
date: 2026-07-20
url: https://simonwillison.net/2026/Jul/20/afraid-of-chinese-models/
category: AI / LLMs / Policy
tags: [ai-policy, chinese-models, distillation, qwen, stratechery, copyright]
ingested: 2026-07-20
---

# Who's Afraid of Chinese Models?

**Source**: Simon Willison (link blog pointing to Stratechery)
**Date**: 2026-07-20
**URL**: https://simonwillison.net/2026/Jul/20/afraid-of-chinese-models/

## TL;DR

Link blog do Simon Willison apontando para o Stratechery de Ben Thompson (*Who's Afraid of Chinese Models?*). A proposta de Thompson, endossada por Simon:

1. **EUA deveria passar lei** que (1) torna explícito que coletar dados para treinar modelos é fair use, e (2) barra termos de serviço que proíbem distillation, pelo menos para empresas americanas.
2. **Argumento**: parar distillation — que é literalmente só querying the API — é quase impossível. EUA deveria ir no caminho oposto e abraçar uma policy que **indemnifica os labs** mas também **garante que o que eles aprenderam alimenta mais inovação para todos**.

Thompson também teoriza que a decisão da Alibaba de lançar Qwen 3.8 Max como open weights (reversal da decisão de **não** lançar Qwen 3.7 Max em maio) pode ter sido influenciada por discurso recente de Xi Jinping:

> "We should seize this rare, historic opportunity to encourage open source, openness, collaboration and sharing."

## A citação central de Thompson

> "The U.S. should pass a law that (1) makes explicit that collecting data for training models is fair use, and (2) bars terms of service that forbid distillation, for U.S. companies at a minimum. Stopping distillation — which is literally just querying the API — is nearly impossible; the U.S. should go the other way and lean into a new copyright policy that both indemnifies the labs and also guarantees that what they learned fuels further innovation for everyone else."

## Por que isso importa

- Tira a hipocrisia dos labs que proíbem distillation nos seus TOS enquanto treinaram em dados unlicensed.
- É movimento estratégico vs. China: se EUA quer competir com modelos chineses open-source, a arma é **abrir ainda mais**, não fechar.
- Conecta com o release de Qwen 3.8 Max — sinal de que China está se movendo agressivamente para o lado open, possivelmente por direção política top-down.

## Notas e Conexões

- [[Stratechery — Ben Thompson]] (paywall, mas public framing já dá tese)
- [[Qwen 3.8 Max release]] — reversal vs. Qwen 3.7
- [[Xi Jinping open source speech]] (Chinese gov policy direction)
- [[Distillation as legal/policy question]]
- [[Training data fairness question]]

## Contexto adicional (via Daring Fireball)

O link também foi destaque por John Gruber no Daring Fireball. Sinaliza que o argumento de Thompson está circulando nos círculos tech-commentary principais.

## Tags de Simon Willison no post

`ai`, `generative-ai`, `llms`, `training-data`, `qwen`, `ai-ethics`, `ai-in-china`