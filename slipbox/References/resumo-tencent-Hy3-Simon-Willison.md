---
title: "tencent/Hy3 — Novo MoE open-weight da Tencent"
source: https://simonwillison.net/2026/Jul/6/hy3/
date: 2026-07-07
tags: [llm, open-source, mistura-de-experts, ia-chinesa, apache-2]
---

# tencent/Hy3 — Novo MoE open-weight da Tencent

A Tencent Hy Team lançou o **Hy3**, um modelo Mixture-of-Experts Apache 2.0 com **295B parâmetros totais, 21B ativos e 3.8B em camadas MTP** (Multi-Token Prediction). O modelo completo pesa 598 GB no Hugging Face; a versão quantizada FP8 cai para 300 GB. Janela de contexto: **256K tokens**. Disponível grátis no OpenRouter até 21 de julho.

O comunicado oficial afirma que Hy3 "outperforms similar-size models and rivals flagship open-source models with 2-5x parameters" após pós-treinamento escalado com dados de alta qualidade vindos de feedback de 50+ produtos internos. É a versão final após o preview de abril.

Simon Willison testou com o benchmark clássico "Generate an SVG of a pelican riding a bicycle" — o modelo entregou uma ilustração coerente, sinal de que segue o padrão de qualidade multimodal/raciocínio dos modelos abertos de ponta. Categorizado como: ai, generative-ai, llms, llm-release, ai-in-china.

## Por que importa

- É mais um sinal de que o eixo da fronteira open-weight se deslocou: labs chineses (Tencent, DeepSeek, Qwen) estão entregando modelos Apache 2.0 com parâmetro counts que rivalizam com modelos fechados de 1-2 anos atrás — sem paywall de API.
- A arquitetura MoE com 21B ativos em 295B totais mostra que a otimização agora é por inferência eficiente, não por contagem bruta de parâmetros. Isso muda a conta de TCO para quem roda self-hosted vs. chama API.
- Free até 21/07 no OpenRouter é uma janela curta para benchmark próprio — vale testar em tarefas do workflow do Ramon antes que a oferta gratuita expire.

## Frases notáveis

> "Hy3 is a 295B-parameter Mixture-of-Experts (MoE) model with 21B active parameters and 3.8B MTP layer parameters ... it outperforms similar-size models and rivals flagship open-source models with 2-5x parameters."

> "It's available for free on OpenRouter until July 21st."
