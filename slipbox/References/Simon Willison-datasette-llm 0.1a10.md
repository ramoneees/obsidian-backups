---
title: "datasette-llm 0.1a10"
source: "Simon Willison"
date: 2026-11-04
url: "https://simonwillison.net/2026/Nov/4/datasette-llm/"
author: "Simon Willison"
category: "Release"
tags: [release, datasette, llm-cli, ia]
blogwatcher_id: 1233
ingested: 2026-11-05
---

# datasette-llm 0.1a10

**Fonte:** Simon Willison
**Data:** 4 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/4/datasette-llm/

## Resumo

Release de correção do datasette-llm, o plugin do Datasette que serve como integração LLM para outros plugins dependerem. O fix corrige um bug que afetava o site de demo agent.datasette.io: o conjunto de modelos LLM disponíveis não estava sendo corretamente restrito aos modelos declarados na configuração.

## Ideias principais

- datasette-llm é plugin de infraestrutura — outros plugins dependem dele para falar com LLMs —, então um bug de restrição de modelos vira bug em cascata para toda a cadeia de dependentes.
- O caso do agent.datasette.io mostra o padrão "config é contrato": o que está na configuração deve ser o único universo visível; expor modelos não configurados quebra a expectativa do operador (custo, privacidade, comportamento).
- Faz parte do mesmo ciclo de releases orientado a agentes do Datasette — ver [[resumo-release-datasette-agent-05a0]] e a [[Simon Willison-datasette-apps 0.3a0]], do mesmo dia.

## Notas e conexões

- [[Simon Willison-datasette-apps 0.3a0]] — release irmã do mesmo dia; essa cobre o lado "hospedar apps", esta o lado "modelos de LLM".
- [[resumo-release-datasette-agent-05a0]] — o Datasette Agent é o consumidor principal dessa integração.
- [[slipbox/References]]
