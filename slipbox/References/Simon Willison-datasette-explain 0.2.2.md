---
source: "Simon Willison"
title: "datasette-explain 0.2.2"
date: 2026-09-20
author: "Simon Willison"
url: https://simonwillison.net/2026/Sep/20/datasette-explain/
category: "Release"
tags: [sqlite, datasette, sql, ferramenta, release]
ingested: 2026-09-21
---

# datasette-explain 0.2.2

**Fonte:** Simon Willison (weblog)
**Data:** 20 de setembro de 2026
**URL:** https://simonwillison.net/2026/Sep/20/datasette-explain/

## Resumo

Release 0.2.2 do plugin `datasette-explain` — explica e valida queries SQL enquanto você as digita no Datasette. Novidade principal: explain plans agora funcionam também em páginas read-only de stored queries. O mote foi a atualização do datasette.simonwillison.net para o Datasette 1.0a40, que inspirou o Simon a embaralhar uma nova versão do plugin.

## Ideias principais

- Feedback de plano de execução *enquanto se digita* — a mesma lógica de linting contínuo aplicada a SQL; barato de construir quando a engine (SQLite) expõe `EXPLAIN QUERY PLAN` de forma acessível.
- Ritmo de release do ecossistema Datasette 1.0: plugins acompanham as alphas do core (1.0a40 → 0.2.2 do explain).

## Notas e conexões

- Continua a série do Datasette 1.0 vista em [[Simon Willison-datasette 0.65.5]] e [[Simon Willison-Release: datasette-auth-github 1.0]].
- Aplicável como inspiração para UIs internas sobre SQLite (cockpit, worklog): um `EXPLAIN` inline em qualquer campo de query aumenta a confiança sem custo.
- [[slipbox/References]]
