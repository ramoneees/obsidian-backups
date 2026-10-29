---
title: "Inline rendering with document​.currentScript"
source: Simon Willison
date: 2026-10-17
url: "https://simonwillison.net/2026/Oct/17/document-currentscript/"
author: "Simon Willison"
category: Link
tags: [javascript, web, truque, link]
ingested: 2026-10-29
---

# Inline rendering with document​.currentScript

**Fonte:** Simon Willison | **Data:** 2026-10-17 | **URL:** https://simonwillison.net/2026/Oct/17/document-currentscript/

## Resumo

Link para o truque da Lean Rada com document.currentScript: uma função de atalho transforma scripts inline numa micro linguagem de template dentro do HTML.

## Ideias principais

- $=(...n)=>document.currentScript.replaceWith(...n) — substitui o próprio script pelo resultado
- Renderização inline sem build step

## Notas e conexões

- [[slipbox/References]]
