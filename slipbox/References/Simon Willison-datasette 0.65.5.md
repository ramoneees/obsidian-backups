---
title: "datasette 0.65.5"
source: "Simon Willison"
date: 2026-09-16
url: "https://simonwillison.net/2026/Sep/16/datasette-2/"
tags: [reference, datasette, release, python, seguranca, simon-willison]
ingested: 2026-09-17
---

# datasette 0.65.5

**Fonte:** Simon Willison (série de releases)
**Data:** 16 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/16/datasette-2/

## Resumo

Release de segurança do datasette 0.65.5 (trilho estável). Correção de uma vulnerabilidade reportada por dpfkdlemtp (GHSA-h547-rmjf-5m2m).

## A vulnerabilidade

- Um **newline à direita no nome da tabela requisitada** podia burlar as permissões de tabela e expor linhas privadas.
- Quem usa controle de permissões por tabela no 0.65.x deve atualizar imediatamente.

## Notas e conexões

- A mesma correção entra no [[Simon Willison-datasette 1.0a40]] (trilho alpha).
- [[slipbox/References]]
