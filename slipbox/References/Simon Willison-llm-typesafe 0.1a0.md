---
source: "Simon Willison"
title: "llm-typesafe 0.1a0"
date: 2026-09-22
url: https://simonwillison.net/2026/Sep/22/llm-typesafe/
author: "Simon Willison"
category: "Release"
tags: [llm, datasette, python, typesafe-ai, jev, ferramentas-dev]
ingested: 2026-09-22
---

# llm-typesafe 0.1a0

**Fonte:** Simon Willison (weblog)
**Data:** 22 de setembro de 2026
**URL:** https://simonwillison.net/2026/Sep/22/llm-typesafe/

## Resumo

Willison soltou um plugin para o LLM CLI que dá acesso ao Jev e outros modelos da TypeSafe AI (o mesmo "decision model" do artigo de ontem). `llm install llm-typesafe`, `llm keys set typesafe`, e então perguntas de três tipos:

- **noul (yes/no):** `llm -m jev 'Please refund my last payment.' -s 'Does this message explicitly request a refund?'` → `{"type": "noul", "noul": 0.99}`
- **choice:** categorias definidas em JSON via `-o answer_type choice -o criteria '{...}'` (ex.: rotear mensagem para billing/technical/other).
- **score:** escala ordinal definida por lista de critérios (ex.: reprodutibilidade de um bug report em 3 níveis).

## Ideias principais

- Fecha o loop do artigo do Jev: decisão tipada (float em vez de texto para parsear) já acessível num CLI de 3 comandos — API key na console.typesafe.ai, waitlist anda rápido.
- O caso de roteamento billing/technical/other é um triage de tickets pronto — padrão diretamente aplicável a fluxos de suporte e classificação em cron.
- Plugin alfa (0.1a0): Willison publicando no dia seguinte ao lançamento do modelo — o ritmo dele de "ver algo novo → versão utilizável em horas".

## Notas e conexões

- Sequência direta de [[Simon Willison-Jev introduces a new shape of LLM - System One, aka Decision Models]]: lá o conceito, aqui a ferramenta.
- O formato de saída JSON tipado elimina o passo frágil de "parse texto do modelo" que qualquer pipeline LLM hoje carrega.
- [[slipbox/References]]
