---
source: "Simon Willison"
title: "commit-rewriter 0.2"
date: 2026-09-24
url: https://simonwillison.net/2026/Sep/24/commit-rewriter/
author: "Simon Willison"
category: "Release"
tags: [git, ferramentas-dev, coding-agents]
ingested: 2026-09-25
---

# commit-rewriter 0.2

**Fonte:** Simon Willison (weblog)
**Data:** 24 de setembro de 2026
**URL:** https://simonwillison.net/2026/Sep/24/commit-rewriter/

## Resumo

Release incremento do commit-rewriter (web app Python para reescrever mensagens de commit em massa — ver [[resumo-commit-rewriter-0-1]] para o contexto do lançamento). Novidade da 0.2: suporte a branches que não são o default — `uvx commit-rewriter --branch other` roda contra outro branch (issue #3 no repo).

## Ideias principais

- Ferramenta mínima, utilidade concreta para o fluxo com coding agents: histórico público gerado por agente precisa de curadoria humana antes do merge.
- O `--branch other` importa para worktrees: o caso de uso real (limpar commits de release num branch de preparação, não no main) funciona sem trocar de checkout.

## Notas e conexões

- `uvx commit-rewriter` — zero instalação, usa o estado do checkout atual e cria branch reversível antes de reescrever.
- Ecossistema: [[Simon Willison-Note on 24th September 2026]] (a disciplina que os agentes exigem) e [[Simon Willison-datasette 1.0a41]] (mesmo autor/dia).
- [[slipbox/References]]
