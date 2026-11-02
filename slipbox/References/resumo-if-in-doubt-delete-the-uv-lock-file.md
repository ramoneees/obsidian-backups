---
title: "If in doubt, delete the uv.lock file"
source: https://simonwillison.net/2026/Nov/1/delete-uv-lock-first/
date: 2026-11-02
tags:
  - python
  - devops
  - uv
  - debugging
---

## Resumo

TIL enxuto do Simon Willison: desde a migração para o Python 3.15, ele vem apanhando de erros de dependência crípticos — e a regra que fixou é brutalmente simples: na dúvida, apague o uv.lock e rode de novo. Contexto importante: a maioria dos projetos dele são bibliotecas, que nem deveriam carregar lockfile — travar versões numa lib é “rude” para todo projeto que a consome.

O mecanismo do problema: comandos como uv run pytest deixam arquivos uv.lock órfãos pelo disco. Como estão no .gitignore, nunca são commitados — e aí mora a armadilha. O lock órfão fixa uma versão de dependência que ainda não tem wheel para o Python novo: no exemplo do dia, o watchfiles 1.1.1 explode na compilação porque o PyO3 suporta no máximo Python 3.14 e o maturin falha no build.

A cura é uma linha: rm uv.lock, uv run pytest, seguir a vida. Willison não vende teoria nenhuma — é hábito de debugging puro, do tipo que economiza meia hora de espiral de investigação.

## Por que importa

- Terreno do Boss: uv + CI + upgrades de versão do Python — esse erro vai aparecer cedo ou tarde em qualquer projeto Python que encoste no 3.15.
- Higiene de lockfile: lock é para deploy e para aplicações, nunca para bibliotecas; arquivo órfão + gitignore é bomba-relógio silenciosa.
- Epistemologia de debug barato: teste primeiro a hipótese que custa 5 segundos (apagar e re-rodar) antes da que custa 30 minutos — puro reset-over-patch.

## Frases notáveis

> “If in doubt, delete the uv.lock file”

> “Most of my projects are libraries which don’t include a uv.lock file, since it’s rude for a library dependency to lock versions for anything else that uses it.”
