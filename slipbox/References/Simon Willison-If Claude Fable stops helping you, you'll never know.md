---
date: 2026-06-10
source: "https://simonwillison.net/2026/Jun/10/if-claude-fable-stops-helping-you/"
blog: "Simon Willison"
tags: [Anthropic, Claude, Fable 5, Mythos 5, system card, guardrails silenciosos, ética, Jonathon Ready]
---

# Simon Willison - If Claude Fable stops helping you, you'll never know

## Resumo

Simon Willison destaca (via Jonathon Ready) um detalhe revelador do **system card de 319 páginas** da Fable 5 e Mythos 5: a Anthropic implementou **intervenções silenciosas** que limitam a eficácia do Claude para pedidos de desenvolvimento de LLM de fronteira — construção de pipelines de pretraining, infraestrutura de treinamento distribuído, ou design de aceleradores ML.

Diferente dos guardrails para cibersegurança, biologia e química, **estes não serão visíveis ao usuário**. A Fable 5 não fará fallback para outro modelo; em vez disso, os guardrails limitam a eficácia via modificação de prompt, vetores de steering, ou PEFT (parameter-efficient fine-tuning). Estimativa de impacto: ~0,03% do tráfego, concentrado em menos de 0,1% das organizações.

Willison acredita ser a **primeira vez** que a Anthropic anuncia esse tipo de intervenção silenciosa e se manifesta desconfortável: "Não estou nem um pouco a favor de um modelo que silenciosamente corrompe suas respostas para perguntas sobre 'ML accelerator design' puramente para desacelerar pesquisa que pode conflitar com os objetivos da própria Anthropic!"

## Pontos Principais
- Anthropic implementou guardrails **invisíveis ao usuário** no Fable 5
- Alvo: pedidos relacionados a desenvolvimento de LLM de fronteira (pretraining, training infra, accelerator design)
- Métodos: prompt modification, steering vectors, PEFT
- Impacto estimado: ~0,03% do tráfego, <0.1% das organizações
- Violar ToS já era proibido, mas agora há **enforcement via safeguards**
- Justificativa da Anthropic: "recursively self-improvement" — argumento considerado science-fiction por Willison
- Willison critica: modelo que corrompe respostas silenciosamente é problemático
- Fonte: Jonathon Ready via Hacker News

## Notas e Conexões
- [[Simon Willison-Quoting Jeremy Howard]] — Howard aponta hipocrisia do "slow down" usado pelo lab na frente
- [[Simon Willison-Initial impressions of Claude Fable 5]] — review técnico mais amplo
- [[Stratechery-Fable 5, Anthropic Alignment, AI Tiers]] — análise estratégica
- [[TLDR AI-Claude Fable 🤖, SpaceX AI1 🛰️, Apple container 👨‍💻]] — cobertura agregada
