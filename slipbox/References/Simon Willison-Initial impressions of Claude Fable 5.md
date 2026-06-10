---
date: 2026-06-09
source: "https://simonwillison.net/2026/Jun/9/claude-fable-5/"
blog: "Simon Willison"
tags: [Anthropic, Claude Fable 5, Mythos 5, review, Opus, 1M context, AI]
---

# Simon Willison - Initial impressions of Claude Fable 5

## Resumo

Willison não teve acesso antecipado ao **Claude Fable 5** mas passou ~5,5 horas testando-o. Impressão inicial: é uma "besta" — lento, caro, e está alegremente engolindo tudo que ele joga. Como nos modelos de fronteira atuais, o desafio é encontrar tarefas que ele **não** consegue fazer.

A Anthropic diz que Fable 5 oferece o mesmo desempenho que Mythos 5, mas com guardrails muito mais estritos. Esses guardrails disparam com frequência suficiente para que a Claude API tenha novos mecanismos para avisar o usuário e até uma **opção de fallback automático para outro modelo** em caso de rejeição. Mythos 5 compartilha as capacidades mas "sem os classificadores de segurança". Especificações: 1M tokens de contexto, 128K max output, knowledge cutoff jan/2026. Preço: 2× Opus 4.5/4.6/4.7/4.8 → $10/M input, $50/M output.

A peça inclui um teste cego interessante: Willison pediu para ambos os modelos listarem seus projetos open source. Opus 4.8 admitiu não ter lista completa confiável; Fable 5 produziu uma lista mais completa e precisa (mas ainda assim imperfeita). O que Willison chama de **"big model smell"** — não só velocidade/custo, mas a sensação de amplitude de conhecimento.

## Pontos Principais
- Lançamento conjunto: Claude Fable 5 (público, com guardrails) e Mythos 5 (mesma capacidade, sem safety classifiers)
- Fable 5 ≠ Mythos 5 apenas em safety; capabilities idênticas
- 1M context, 128K max output, cutoff jan/2026
- Preço dobrou em relação à linha Opus 4.5–4.8
- API tem novo mecanismo de notificação quando guardrails disparam
- Opção de fallback automático para outro modelo em caso de rejeição
- "Big model smell": sensação de amplitude de conhecimento, não só capacidade
- Willison escreveu (quase) inteiramente o release do LLM 0.32a3 com Fable 5 — ver post seguinte
- Upgrade guide da Anthropic é mais fino que o de Opus 4.8

## Notas e Conexões
- [[Simon Willison-llm 0.32a3]] — release do LLM escrito majoritariamente por Fable 5
- [[Simon Willison-If Claude Fable stops helping you, you'll never know]] — guardrails silenciosos
- [[Simon Willison-Setting a custom price for a model in AgentsView]] — uso prático com AgentsView
- [[Simon Willison-Quoting Andrej Karpathy]] — reação de Karpathy ao mesmo lançamento
- [[Stratechery-Fable 5, Anthropic Alignment, AI Tiers]]
- [[TLDR AI-Claude Fable 🤖, SpaceX AI1 🛰️, Apple container 👨‍💻]]
