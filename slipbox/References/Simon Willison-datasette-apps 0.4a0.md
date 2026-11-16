---
title: "datasette-apps 0.4a0"
source: "Simon Willison"
date: 2026-11-15
url: "https://simonwillison.net/2026/Nov/15/datasette-apps/"
tags: [reference, datasette, release, datasette-apps, urls, simon-willison]
blogwatcher_id: 1362
ingested: 2026-11-16
---

# datasette-apps 0.4a0

**Fonte:** Simon Willison (série de releases)
**Data:** 15 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/15/datasette-apps/

## Resumo

Datasette Apps são aplicações HTML/JS sandboxadas que vivem dentro do Datasette — "Claude Artifacts, mas podem rodar queries SQL contra seus dados". A 0.4a0 adiciona **linking entre apps**.

## Ideias principais

- **Links com `#fragments`:** dá para linkar um app com fragmentos na URL, e o app enxerga e usa esses fragmentos (ex.: app de detalhe de um registro específico).
- **URL schemes reportados ao Datasette Agent:** os esquemas suportados voltam para o agente, que pode escrever apps que linkam entre si — um app de busca que aponta para as representações no app de detalhe.
- Padrão emergente: **ecossistema de mini-apps compostáveis** dentro de uma instância Datasette, em vez de um app monolítico.

## Notas e conexões

- Alpha anterior: [[Simon Willison-datasette-apps 0.3a0]].
- O Datasette Agent é a outra ponta da integração: [[Simon Willison-datasette-agent 0.6a0]] (mesmo dia).
- [[slipbox/References]]
