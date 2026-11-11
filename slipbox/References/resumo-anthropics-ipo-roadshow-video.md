---
title: "Anthropic's IPO roadshow video"
source: https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/
date: 2026-11-11
tags: [ia, anthropic, recursive-self-improvement, infraestrutura]
---

Simon Willison destrinchou o vídeo do roadshow de IPO da Anthropic (sem transcrição oficial, ele extraiu uma com MacWhisper). O material revela detalhes inéditos de como o negócio da Anthropic funciona por dentro — e o trecho mais quente é o "Approach to compute" com o cofundador Tom Brown.

A Anthropic treina e serve o Claude nas quatro grandes famílias de chips: AWS Trainium, TPUs do Google, NVIDIA e AMD. Essa estratégia multi-chip era considerada loucura — cada chip exige seu próprio stack de software e inferência, caro e difícil de manter. Eles fizeram por anos e viraram especialistas. A prova de maturidade: quando começaram com GPUs AMD este ano, o que antes levava meses e dezenas de engenheiros foi feito pelo agente Mythos em três dias, "sem praticamente intervenção humana" — o próprio Claude escreveu ou portou ~100% dos kernels.

O segundo pilar é o que eles chamam de "compute multipliers": otimizações que multiplicam o compute efetivo (o produto de capacidade física × multiplicadores descobertos). Um multiplicador 4x significa treinar o mesmo modelo com 25% do compute — ou um modelo muito mais inteligente com o mesmo compute. Os multiplicadores se acumulam entre si, criando vantagem competitiva difícil de replicar.

E vem o trecho que Simon destacou com a tag "recursive-self-improvement": a Anthropic afirma abertamente, num documento de vendas para investidores, que isso acelera ainda mais perto da auto-melhoria recursiva — o Claude descobrirá multiplicadores sozinho, cada vez mais rápido. Agente de IA portando infraestrutura de chips e retórica de RSI em pitch de IPO: o loop agente→infraestrutura→agente deixou de ser teoria e virou slide de investor relations.

## Por que importa
- Agentes de IA já fazem trabalho de infraestrutura de nível sênior (portar kernels entre arquiteturas de GPU) — exatamente o tipo de automação que o Ramon persegue no dia a dia, só que em escala de datacenter.
- A retórica de "recursive self-improvement" num roadshow de IPO é material cru para o cruzamento teologia×tecnologia: a indústria vendendo uma escatologia de salvação técnica.
- Sinal de mercado: multi-chip como hedge de sobrevivência — paralelo útil com o próprio princípio do Ramon de não depender de um único provedor (LiteLLM roteando vários modelos).

## Frases notáveis
> "This time, we had Mythos try it out. It got Claude running on AMD in just three days, with basically no human intervention. Claude ported or wrote almost 100% of the kernels."

> "We believe that this can accelerate even further as we approach recursive self-improvement. Claude will be able to discover compute multipliers entirely by itself."
