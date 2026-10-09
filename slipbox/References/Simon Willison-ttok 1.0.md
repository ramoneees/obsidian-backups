---
title: "ttok 1.0"
source: "Simon Willison"
date: 2026-10-09
url: "https://simonwillison.net/2026/Oct/9/ttok/"
category: "Release"
tags: [reference, llm, tokenizer, tiktoken, release, simon-willison]
ingested: 2026-10-09
---

# ttok 1.0

**Fonte:** Simon Willison (release)
**Data:** 9 de outubro de 2026
**URL original:** https://simonwillison.net/2026/Oct/9/ttok/

## Resumo

Logo após soltar o ttok 0.4, Simon rodou `uv tool upgrade ttok`, canalizou um arquivo e percebeu que a ferramenta estava usando o tokenizer do GPT-4 como default — quando o óbvio agora é o GPT-5/GPT-6. Trocar o default foi desculpa suficiente para finalmente marcar uma versão **1.0**.

Detalhe interessante de due diligence: a OpenAI **nunca confirmou oficialmente** que o GPT-6 usa o mesmo tokenizer da família GPT-5 (existe uma issue "angry" sobre isso). Simon se baseou num experimento do William Liu: **os sete modelos GPT atuais (5.5, 5.6 Sol/Terra/Luna, 6 Astra/Sol/Luna) reportam exatamente 44.794 tokens e casam entre si nos 31 fixtures** do corpus de teste — GPT-6 não muda a contagem de input.

## Notas principais

- ttok = CLI para contar/truncar texto por tokens, via tiktoken (open source da OpenAI).
- 1.0 = mudança do tokenizer default para a família GPT-5/6, não mudança de API.
- Evidência comunitária (commit + fixtures) no lugar de confirmação oficial do vendor — padrão útil para decidir sob incerteza.

## Notas e conexões

- Sequência direta de [[Simon Willison-ttok 0.4]] (mesma semana).
- Tokenizer compartilhado entre GPT-5.x e GPT-6 simplifica estimativa de custo/contexto entre gerações.
- [[slipbox/References]]
