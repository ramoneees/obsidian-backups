---
title: "OpenAI DevDay 2026 live blog"
source: Simon Willison
date: 2026-09-30
url: https://simonwillison.net/2026/Sep/29/openai-devday-2026-live-blog/
author: Simon Willison
category: Live Blog
tags: [openai, devday, dots, gpt-6.1-sol, ultrafast, chatgpt-sites, codex, sign-in-with-chatgpt]
ingested: 2026-10-03
---

# OpenAI DevDay 2026 live blog

**Fonte**: Simon Willison (Simon Willison)
**Data**: 2026-09-30 . **URL**: https://simonwillison.net/2026/Sep/29/openai-devday-2026-live-blog/

## Resumo

Live blog completo do OpenAI DevDay 2026 (Fort Mason, San Francisco; Simon com convite e lugar na área de "creators"). O anúncio central é **Dots** ("powered by Astra"): agentes pessoais com nome e avatar à escolha (o de Simon no Muse é um pelicano), muito semelhantes ao Muse da Meta — "This UI really does look like Meta's Muse agent, currently still at number one on the iOS App Store free list" — disponíveis para Pro e Enterprise. Vêm com ChatGPT Space (artefatos partilhados com slash menu estilo Notion), integração em Slack com identidade própria (resposta da OpenAI ao Claude Tag) e "specialist dots" para legal, finanças e parceria com Microsoft 365. Na plataforma: GPT-6.1 Sol ("Near-Astra level intelligence at a fifth of the price"), Ultrafast (8x mais rápido, até 300 tokens/s, 6x o preço), plano Pro 500 (25x o uso do Plus), Decisions API (Luna escolhendo entre opções pré-definidas, resposta "in a fraction of a second" — resposta ao Jev), Codex open source e "fully in the cloud", Codex Security Cloud, Agents API com Computer Use, e no fim Sign In with ChatGPT ("I've wanted this one for years!"), plugin extensions, ChatGPT Sites (com base SQLite, tarefas agendadas e plugins) e OpenAI Marketplace.

## Ideias principais

- **Dots = Muse da OpenAI**: agente pessoal persistente que pode usar o Codex no laptop para construir e lançar apps; Sam chama o Astra de "our most aligned model" para justificar confiar ao Dot "as much responsibility as you are comfortable with". Por defeito, dots não têm acesso a tudo o que foi partilhado com o ChatGPT.
- **Economia "outcome per dollar"**: Thibault Sottiaux diz que o que importa é quantas tarefas saem por assinatura, não o uso de tokens; o 6.1 Sol é "incredibly efficient" e o Ultrafast "made building impossible things possible" (fundiu os apps desktop ChatGPT e Codex em 28 dias).
- **Segurança com agentes no ciclo**: no Codex Security, um sprint interno com 1/4 dos engenheiros de produto corrigiu 53 findings críticos no primeiro dia; 36% das descobertas eram duplicadas (desduplicação no CLI), e o `codex-security patch` abre PRs com apenas 1% de rollback graças a um `verify-fix` "adversarial" contra o patch.
- **Sinais de maturação da distribuição**: Sign In with ChatGPT deixa utilizadores usarem em apps de terceiros os tokens que já pagam; ChatGPT Sites já aloja 8M sites com 70% dos funcionários da OpenAI a criar os seus; WebMCP é "much more efficient" que Computer Use.
- **Frase-síntese de Thibault**: "Everyone will become a builder. Everyone will create. Developers will also turn into builders - and manual development of code isn't really something that will exist."

## Notas e conexoes

[[slipbox/References]]
