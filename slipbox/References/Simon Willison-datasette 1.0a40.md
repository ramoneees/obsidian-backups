---
title: "datasette 1.0a40"
source: "Simon Willison"
date: 2026-09-16
url: "https://simonwillison.net/2026/Sep/16/datasette/"
tags: [reference, datasette, release, python, seguranca, simon-willison]
ingested: 2026-09-17
---

# datasette 1.0a40

**Fonte:** Simon Willison (série de releases)
**Data:** 16 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/16/datasette/

## Resumo

Release do datasette 1.0a40 no trilho alpha do 1.0. Inclui a mesma correção de segurança do 0.65.5 (bypass de permissões de tabela via newline no nome) mais novos recursos e correções de bugs.

## Destaques

- Plugins agora podem lançar e gerenciar **background tasks** via novo método `datasette.add_background_task()` (contribuição de Alex Garcia).
- Migração para **httpx2** (pydantic) — usada por exemplo no cliente interno `datasette.client.get()`.
- Vários bug fixes, muitos vindos do esforço de triagem de issues rumo ao release 1.0 estável.
- Changelog completo em docs.datasette.io.

## Notas e conexões

- Mesma correção de segurança do patch [[Simon Willison-datasette 0.65.5]] — quem está no trilho 0.65.x deve atualizar para 0.65.5; quem testa os alphas, para 1.0a40.
- [[slipbox/References]]
