---
title: "EmbeddingGemma 2"
source: Simon Willison
date: 2026-10-06
url: https://simonwillison.net/2026/Oct/6/hn-49983751/
author: Simon Willison
category: comment
tags: [ia, embeddings, gemma, google, lock-in, pesos-abertos]
ingested: 2026-10-07
---

# EmbeddingGemma 2

**Fonte**: Simon Willison (comentário no Hacker News)
**Data**: 2026-10-06 . **URL**: https://simonwillison.net/2026/Oct/6/hn-49983751/

> "For embedding models in particular, I don't think it makes sense to use a closed, proprietary, hosted-only model."

## Resumo

Comentário do Simon no HN sobre o EmbeddingGemma 2 (Google, licença Apache 2.0): para embeddings, pesos abertos não são ideologia — são economia. A maior parte das aplicações calcula milhares ou milhões de vetores e os armazena para comparação futura. Se o modelo for fechado e o vendor descontinuá-lo, você paga para recalcular tudo — e a única garantia é a esperança. Ele não quer hostear o modelo: quer pagar um provedor sabendo que, se um dia pararem, existe o caminho dos pesos abertos (rodar ele mesmo ou achar outro vendor).

## Ideias principais

- **Embeddings invertem a economia de LLMs**: o ativo acumulado é o vetor armazenado, não a inferência. Trocar de modelo invalida o arquivo inteiro — recalcular milhões de embeddings é o lock-in real.
- **Open weights como seguro, não como plano A**: hosted-first com escape hatch. O valor da licença Apache 2.0 é a opção de saída, exercida só se necessário.
- **Precedente frágil**: a OpenAI pagou re-embedding em abril de 2024 quando deprecou modelos — cortesia de vendor, não direito do cliente. Não escalável como política de mercado.

## Notas e conexoes

- Mesmo princípio do vault local do Boss: dados em formato aberto (Markdown) com soberania garantida pelo formato, não por política — a nota [[Asian Efficiency-I Don't Migrate My Notes Anymore]] aplica o argumento a apps de notas.
- [[slipbox/References]]
