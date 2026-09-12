---
title: "So you want to use OpenRouter?"
source: "Simon Willison"
date: 2026-09-11
url: "https://simonwillison.net/2026/Sep/11/so-you-want-to-use-openrouter/"
tags: [reference, simon-willison, openrouter, llms, ia, apis, roteamento]
ingested: 2026-09-12
---

# So you want to use OpenRouter?

**Fonte:** Simon Willison (link post → mmoustafa.com, via Hacker News)
**Data:** 11 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/11/so-you-want-to-use-openrouter/
**Linkado:** https://mmoustafa.com/blog/so-you-want-to-use-openrouter/

## Resumo

O OpenRouter se vende com "fallbacks automáticos e escolha da opção mais custo-efetiva por request": um endpoint só, roteado para o melhor backend disponível. Mohamed Moustafa enumera como isso cria problemas: **provedores diferentes rodam software de serving diferente**, com otimizações e settings diferentes — o mesmo endpoint pode servir requests que se comportam de formas diferentes para o mesmo modelo.

## Ideias principais

- Alguns provedores sequer têm capacidade de visão para modelos de visão.
- O processamento da opção `reasoning effort` também varia entre provedores.
- Mitigação: controlar o roteamento com a opção **`provider.only`** (restringe a provedores específicos).
- O método **`/endpoints`** devolve a lista de provedores disponíveis para um model ID específico — útil para auditar antes de travar o roteamento.

## Notas e conexões

- Relevante para qualquer setup com camada de abstração de provider (OpenRouter, LiteLLM): "mesmo modelo" ≠ "mesmo comportamento" quando o backend muda. Testar o modelo no provedor efetivamente usado.
- Conecta com [[Simon Willison-GLM-5.2 is probably the most powerful text-only open weights LLM]] — mesma questão de fundo: modelo aberto/roteável, comportamento dependente de quem serve.
- [[slipbox/References]]
