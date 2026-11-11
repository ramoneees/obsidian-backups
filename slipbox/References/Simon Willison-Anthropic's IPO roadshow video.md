---
title: "Anthropic's IPO roadshow video"
source: Simon Willison
date: 2026-11-11
url: https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/
author: "Simon Willison"
category: Link Blog
tags: [simonwillison, anthropic, ipo, infraestrutura-ia, chips, claude]
ingested: 2026-11-11
blogwatcher_id: 1306
---

# Anthropic's IPO roadshow video

**Fonte:** Simon Willison (Link Blog) | **Data:** 2026-11-11 | **URL:** https://simonwillison.net/2026/Nov/11/anthropic-ipo-roadshow/

## Resumo

Link post: a Anthropic abriu ontem o roadshow do seu IPO, e o vídeo traz informações inéditas sobre como o negócio funciona. O destaque de Simon é a seção "Approach to compute", com o cofundador Tom Brown: como a Anthropic treina e serve Claude nas quatro grandes famílias de chips — AWS Trainium, TPUs do Google, GPUs NVIDIA e (desde este ano) GPUs AMD. Sem transcript oficial do vídeo, Simon extraiu um por conta própria com MacWhisper e destacou os trechos principais.

## Ideias principais

- **Aposta multi-chip precoce e não convencional**: cada chip exige sua própria stack de software e de inferência — caro e difícil de construir; a Anthropic faz isso há anos e transformou o domínio em vantagem competitiva ("we train and serve Claude now across all four major chip families")
- **Claude portando o próprio Claude**: a integração com GPUs AMD, que antes exigia "dezenas de engenheiros por meses", ficou a cargo do Mythos — três dias, praticamente sem intervenção humana, com Claude escrevendo/portando ~100% dos kernels
- **Compute multipliers**: a métrica da casa é o *total effective compute* — capacidade física × multiplicadores descobertos; um multiplicador de 4x permite treinar o mesmo modelo com 1/4 do compute, ou um modelo que antes exigiria 400 unidades com as mesmas 100
- **Os multiplicadores se empilham**: cada descoberta amplifica as anteriores; a aposta é que a curva acelere na aproximação da auto-melhoria recursiva — Claude descobrindo multiplicadores por conta própria, cada vez mais rápido
- Pré-história da estratégia: o postmortem de setembro último já indicava a infraestrutura multi-chip, com bugs que afetavam apenas os deployments em TPU

## Notas e conexões

- Receita trimestral no pré-IPO: [[Simon Willison-Anthropic tells investors quarterly revenue up nearly 50% to $16.8bn ahead of IPO]]
- Infraestrutura multi-chip sob stress: [[Simon Willison-'They screwed us' Personality clashes sent Anthropic's models offline]]
- Plugin oficial na mesma semana: [[Simon Willison-llm-anthropic 0.31]]
- [[slipbox/References]]
