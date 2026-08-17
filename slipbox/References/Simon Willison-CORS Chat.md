---
title: "CORS Chat"
source: "Simon Willison"
date: 2026-08-15
url: "https://simonwillison.net/2026/Aug/15/cors-chat/"
tags: [reference, tools, cors, openai-api, lm-studio, openrouter]
ingested: 2026-08-17
---

# CORS Chat

**Fonte:** Simon Willison
**Data:** 15 de agosto de 2026
**URL original:** https://simonwillison.net/2026/Aug/15/cors-chat/

## Resumo

Ferramenta nova: [CORS Chat](https://tools.simonwillison.net/cors-chat) — conversar diretamente com qualquer endpoint compatível com a API OpenAI Responses que envie headers CORS, inteiramente no browser. Construída em um dia (com GPT-5.6-Sol xhigh) para testar o Qwen 3.8 27B rodando em LM Studio no MacBook e no NVIDIA DGX Spark.

## Notas principais

- **Casos testados:** LM Studio com a flag `--cors` e OpenRouter — ambos funcionam.
- **Features:** endpoints configuráveis com headers custom, conversas persistidas localmente (export como JSON copy-paste), múltiplas sessões com modelos e configurações de reasoning diferentes.
- **Detalhe divertido:** detecta SVGs sendo gerados e renderiza progressivamente enquanto os tokens ainda chegam via streaming.
- Padrão Simon: ferramenta mínima de página única que resolve um problema real do próprio fluxo de testes, lançada como utilidade pública.

## Conexões

- Ferramenta: https://tools.simonwillison.net/cors-chat
- Motivação direta: [[Simon Willison-Qwen 3.8 27B Overthinking]] (testar esse modelo local).
- Tópicos: [[CORS]], [[OpenAI Responses API]], [[LM Studio]], [[local LLMs]].
