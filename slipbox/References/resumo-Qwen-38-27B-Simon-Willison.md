---
title: "Qwen 3.8 27B: o modelo pequeno que empora os gigantes"
source: https://simonwillison.net/2026/Aug/17/qwen-38-27b-scores-52/
date: 2026-08-18
tags: [ia, llms, modelos-locais]
---

# Qwen 3.8 27B: o modelo pequeno que empora os gigantes

O Qwen 3.8 27B, da Alibaba, cravou 52 no Artificial Analysis Intelligence Index — o mesmo placar do GPT-5.6 Luna (max) e a apenas um ponto do GLM-5.2 (753B) e do DeepSeek V4 Pro (1,7 trilhão de parâmetros). A ironia é deliciosa: um modelo de 27B, que roda em um laptop razoável com um arquivo de 17GB, está brigando no mesmo placar de monstros de quase dois trilhões de parâmetros. A Distiliação e o treinamento melhorado estão comprimindo o que antes exigia datacenter.

No uso prático (relatado no post-companheiro de 16/08), Simon Willison rodou o modelo em um MacBook Pro M5 Max de 128GB e num NVIDIA DGX Spark, via LM Studio com quantização Q4_K_M. O veredito técnico: excelente em visão e bounding boxes, gerou o melhor "pelicano de bicicleta" em SVG que ele já conseguiu localmente. Mas há um porém devastador: o padrão de fábrica é `xhigh` de reasoning effort, o que leva o modelo a superpensar absolutamente tudo — 21 minutos e 22 mil tokens de raciocínio para desenhar um ciclista de penas.

A recomendação prática é ignorar o default e rodar em `low` ou sem raciocínio. Com raciocínio desligado, o mesmo prompt caiu para ~2 minutos — embora a qualidade visível caia junto (o pedal mais fraco). É um trade-off que quem roda LLMs localmente precisa conhecer: o overhead de raciocínio consome contexto e paciência em hardware de consumo.

## Por que importa

- **A fronteira está descendo para o hardware local.** Modelos Apache 2.0 de 27B pontuando como gigantes proprietários muda a economia de qualquer pipeline que Ramon rode em casa — sem API, sem custo por token, sem enviar dados para fora.
- **Defaults importam mais do que benchmarks.** Um modelo excelente com um default terrível (`xhigh` para tudo) é uma armadilha operacional: em automação/agents, esse comportamento queima tempo e contexto silenciosamente.
- **A corrida chinesa de modelos abertos continua acelerando** — Qwen, GLM e DeepSeek alternando a liderança em open weights é o novo normal, não exceção.

## Frases notáveis

> "That's the same score as GPT-5.6 Luna (max), and just one point behind GLM-5.2 (max) and DeepSeek V4 Pro 0813 (max) — that GLM is 753B and that DeepSeek is 1.7T parameters."

> "My strong recommendation: ignore that default. Run Qwen 3.8 27B on low or even no reasoning levels at first. It's a great model, but wow that default setting is a bad place to start."
