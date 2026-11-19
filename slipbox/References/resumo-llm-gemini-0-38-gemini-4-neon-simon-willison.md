---
title: "llm-gemini 0.38 e o lineup confuso do Gemini 4 (Neon)"
source: https://simonwillison.net/2026/Nov/18/llm-gemini/
date: 2026-11-19
tags: [llm, gemini, ia, custos]
---

Google lançou o Gemini 4 Neon e o plugin llm-gemini 0.38 do Simon Willison já dá acesso. O ponto central do post não é o modelo em si, mas o caos de pricing: o lineup Gemini 4 (Carbon, Neon, Hydrogen, agora sem Argon) já era confuso, e o Neon "de alguma forma deixou ainda pior".

A armadilha: no papel, a ordem de preço é Hydrogen ($1,50/$7,50 por 1M in/out) < Carbon ($4/$20) < Neon ($3/$15). Mas o Carbon está com promo de 50% até 30/11 ($2/$10), então hoje o Neon é o mais caro dos três e o Carbon é o segundo mais barato. Só em 1º de dezembro, quando a promo expira, o lineup "faz sentido". E o anúncio do Neon simplesmente finge que o Argon não existe — modelo que era idêntico em preço ao Carbon.

Willison fez o dever de casa com o teste padrão dele (pelican riding a bicycle) nos três modelos × níveis de thinking (low/medium/high/xhigh). Os números expõem o que o preço por token esconde: na mesma tarefa, Carbon high custou 20,31 cents e levou 4m11s; Neon high, 14,55 cents e 1m11s; Hydrogen low, 2,25 cents e 19s. Qualidade cai de Carbon → Neon → Hydrogen e de high → low, mas a escala de custo por resultado é muito maior que a de qualidade.

A lição prática para qualquer pipeline de LLM: o custo real é função de (modelo × nível de thinking × latência), não da tabela de preço por token — e promoções expirando (1/12) mudam a escolha ótima de modelo da noite pro dia.

## Por que importa

- Roteamento de modelos é exatamente o jogo do Ramon (LiteLLM no VPS, fleet zai-glm): a grade qualidade × custo × latência do Willison é o template da decisão "qual modelo pra qual tarefa".
- Alerta de custo: naming confuso + pricing promocional que expira é a armadilha clássica de pipeline de LLM em produção — vale checar qualquer modelo "barato" fixado antes do vencimento da promo.
- O post é um bom modelo do gênero "release note com análise": dado empírico próprio (pelicans) em vez de copiar o slide de marketing do Google.

## Frases notáveis

> "The Neon announcement pretends that Argon doesn't exist."

> "I wrote recently about how confusing the pricing for the Gemini 4 series was — Neon has somehow made this even worse."
