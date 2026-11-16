---
title: "datasette-agent 0.6a0"
source: "Simon Willison"
date: 2026-11-15
url: "https://simonwillison.net/2026/Nov/15/datasette-agent/"
tags: [reference, datasette, release, llm, ai, agentes, simon-willison]
blogwatcher_id: 1363
ingested: 2026-11-16
---

# datasette-agent 0.6a0

**Fonte:** Simon Willison (série de releases)
**Data:** 15 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/15/datasette-agent/

## Resumo

Lote de correções acumuladas do Datasette Agent, o plugin de agente do Datasette que responde perguntas sobre seus dados. Destaque: o prompt do agente agora aparece **direto na homepage do Datasette**, com suporte a hash-mentions de tabelas e queries.

## Ideias principais

- **Hash-mentions:** referenciar `#tabela` e `#query` diretamente no prompt — o contexto certo entra na conversa sem configuração.
- Agente como superfície de entrada do produto: em vez de plugin escondido, a camada de IA vira a porta de entrada da homepage.

## Notas e conexões

- Alpha anterior: [[Simon Willison-datasette-agent 0.4a0]].
- Integra com o linking novo dos apps: [[Simon Willison-datasette-apps 0.4a0]] — o agente escreve apps que linkam entre si.
- [[slipbox/References]]
