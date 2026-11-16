---
title: "datasette 0.65.6"
source: "Simon Willison"
date: 2026-11-15
url: "https://simonwillison.net/2026/Nov/15/datasette-2/"
tags: [reference, datasette, release, seguranca, python, simon-willison]
blogwatcher_id: 1361
ingested: 2026-11-16
---

# datasette 0.65.6

**Fonte:** Simon Willison (série de releases)
**Data:** 15 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/15/datasette-2/

## Resumo

Release de segurança no trilho estável: backport de um fix menor vindo do [[Simon Willison-datasette 1.0a43]]. Quem roda 0.65.x com permissões deve atualizar.

## A vulnerabilidade

- Um banco registrado com `add_database(db, name=..., route=...)` em que o **route difere do name** podia ser baixado via `/<route>.db` por atores com acesso negado a ele — a checagem de permissão olhava o nome, não a rota.

## Notas e conexões

- Correção irmã da falha de queries privadas expostas na alpha: [[Simon Willison-datasette 1.0a43]].
- Série de fixes de segurança do datasette no vault: [[Simon Willison-datasette 0.65.5]] (newline em nome de tabela burlando permissões).
- [[slipbox/References]]
