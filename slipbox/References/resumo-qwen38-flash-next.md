---
title: "Qwen3.8-Flash-Next"
source: "https://simonwillison.net/2026/Aug/26/qwen38-flash-next/"
date: 2026-08-27
tags: [ia, llms, qwen, modelos-open-weights]
---

# Qwen3.8-Flash-Next

A Qwen liberou mais um modelo open weights: o Qwen3.8-Flash-Next, um MoE multimodal que funciona como preview antecipado da arquitetura que será usada no Qwen4. Simon Willison destaca os números: 125B de parâmetros totais, mas apenas 6B ativos por token — desempenho de modelo grande com custo de inferência de modelo pequeno.

Willison testou no hardware da moda para a categoria, um NVIDIA DGX Spark, usando as quantizações GGUF da Unsloth (72,5GB UD-IQ1_S e 78,9GB UD-Q2_K_XL). O teste de fidelidade dele, como sempre, é o clássico "pelican riding a bicycle" — gerar SVG de um pelicano de bicicleta virou benchmark informal da comunidade para medir se o modelo realmente entende instruções espaciais e visuais. O resultado favorito saiu do quant Q2 com raciocínio em esforço "xhigh".

O sinal importante é estratégico: a linha Qwen segue agressiva em open weights, e o Flash-Next indica que a arquitetura do Qwen4 já está sendo validada em produção. Para quem roda modelos localmente, MoE com poucos parâmetros ativos é a tendência dominante — qualidade de 100B+ com orçamento de 6B.

## Por que importa

- O Boss roda Qwen local (qwen3.8-max para visão): a arquitetura Flash-Next antecipa o que vem no Qwen4 e pode redefinir o custo-benefício do setup local em breve.
- MoE com 6B ativos é o argumento técnico de que "modelo grande local" deixou de ser contradição — relevante para a estratégia de split IA pesado-cloud vs. privado-local.
- A régua de avaliação da comunidade (pelicano de bicicleta em SVG) é um lembrete divertido de que benchmark prático > benchmark de papel.

## Frases notáveis

> "Another open weights model from Qwen. This one is 'a multimodal MoE model that also serves as an early preview of the architecture used in Qwen4'."

> "It's pretty big: 125B tokens, but only 6B active which means it gets a significant performance boost."
