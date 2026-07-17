---
title: "Kimi K3, and what we can still learn from the pelican benchmark"
source: https://simonwillison.net/2026/Jul/16/kimi-k3/
date: 2026-07-17
tags: [ia, llm, moonshot, kimi, llm-benchmark, devops]
---

# Kimi K3 e o Que Ainda Podemos Aprender com o Benchmark do Pelicano

Simon Willison analisa o lançamento do Kimi K3 pela Moonshot AI — modelo de 2,8T de parâmetros, rotulado como o primeiro "open 3T-class model" do mercado chinês. No Artificial Analysis Intelligence Index, K3 atinge Elo 1547, ficando atrás apenas do Claude Fable 5; preço de $0,94/tarefa, ~metade do Opus 4.8. Lidera também a Arena.ai Frontend Code. Custo de API: $3/$15 por milhão de tokens — o mais caro já cobrado por um laboratório chinês, igualando a faixa do Claude Sonnet.

Willison aproveita o lançamento para revisitar seu famoso teste do "pelicano de bicicleta" (SVG gerado via prompt), hoje com 21 meses. O artigo é honesto: reconhece que o teste perdeu correlação com capacidade real, principalmente para comparar modelos agentic. Mas continua útil como forcing function para rodar a API, obter uma estimativa rápida de raciocínio/custo e verificar capacidade de saída em SVG e visão. No caso do K3, revelou: (a) só tem um nível de raciocínio ("max") — consumiu 13.241 reasoning tokens para gerar um pelicano; (b) prompt "hi" custa 86 tokens, sugerindo system prompt oculto de ~85 tokens; (c) o pelicano custou 25 centavos.

## Por que importa

- Discute criticamente benchmark vs. capacidade real em LLMs, tema caro a quem opera IA em produção: correlação pura fica obscura quando os modelos começam a otimizar para benchmarks específicos ou quando a capacidade agentic (tool calling, longas cadeias) não aparece nos rankings.
- O caso do system prompt oculto do K3 (refused to leak it) é prático para quem trabalha com auditoria de modelos chineses e precisa entender o que está "grátis" no input billing.
- K3 marca uma inflexão: laboratório chinês competitivo com Claude e GPT no topo, com preço alinhado ao Sonnet — fim da era do "barato e bom" do open-weight chinês, relevante para decisões de stack em devops/IA.

## Frases notáveis

> "It only has one reasoning effort right now, 'max' — and it shows. The model consumed 13,241 reasoning tokens to output 3,417 tokens of response."

> "My pelican test is 21 months old now... The biggest limitation of the pelican is that it doesn't touch at all on the thing that matters most for today's model: agentic tool calling and the ability to operate tools reliably as conversations grow in length."
