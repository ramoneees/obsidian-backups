---
title: "llm-openai-decisions 0.1a0"
source: Simon Willison
date: 2026-10-06
url: https://simonwillison.net/2026/Oct/6/llm-openai-decisions/
author: Simon Willison
category: release
tags: [ia, llm, openai, plugins, jev, decisao]
ingested: 2026-10-07
---

# llm-openai-decisions 0.1a0

**Fonte**: Simon Willison (release)
**Data**: 2026-10-06 . **URL**: https://simonwillison.net/2026/Oct/6/llm-openai-decisions/

> Plugin LLM para a nova OpenAI Decisions API — a resposta da OpenAI ao formato Jev.

## Resumo

A OpenAI lançou a Decisions API (estilo Jev, anunciada na DevDay da semana passada) e Simon publicou o plugin `llm-openai-decisions` para acessá-la via CLI `llm`. Ele não escreveu o plugin à mão: fez o GPT-6 Astra ler a documentação nova e construir o plugin inspirado no `llm-typesafe` existente (que fala com o Jev). O modelo `gpt-6-luna` aceita entrada de imagem além de texto; ambos cobram só por input — OpenAI a 10 cents/milhão de tokens, Jev a 4,2 cents. A API mantém os três tipos de pergunta do Jev: yes/no, escolhas e scores.

## Ideias principais

- **API de decisões como primitiva barata**: classificação estruturada (sim/não, escolha, nota) por centavos por milhão de tokens de input — o componente econômico para agentes julgarem milhões de itens sem LLM caro no loop.
- **Doc → código por IA**: o plugin nasceu de um prompt ("leia a doc e construa inspirado no llm-typesafe"), padrão de desenvolvimento em que a documentação bem escrita vira implementação quase direta.
- **Imagem no decision model**: `gpt-6-luna` classifica imagens ("esta imagem contém mamíferos?") — decisão multimodal pelo mesmo preço de entrada.

## Notas e conexoes

- Contexto dos anúncios em [[Simon Willison-OpenAI DevDay 2026 live blog]].
- Mesma leva de releases que [[Simon Willison-llm-mistral 0.16]] — o ecossistema de plugins `llm` acompanhando cada provedor.
- [[slipbox/References]]
