---
title: "Quoting Charity Majors"
source: "Simon Willison's Weblog"
date: 2026-06-17
url: https://simonwillison.net/2026/Jun/17/charity-majors/
author: "Charity Majors (quoted by Simon Willison)"
category: "Quotation"
tags: [ai, engineering, discipline, code-economics, generative-ai, charity-majors, simon-willison]
ingested: 2026-06-17
---

# Quoting Charity Majors

## Fonte
Simon Willison's Weblog

## Data
2026-06-17

## URL
https://simonwillison.net/2026/Jun/17/charity-majors/

## Resumo

Post de citação (Willison) de **Charity Majors** (CTO da Honeycomb, voz influente em observability/engineering) — extraído de "AI demands more engineering discipline. Not less":

> "What happened in 2025 was this: **the economics of code production were turned upside down**. Instead of being very hard, time-consuming, and expensive to generate code, it became effectively free and instant. Lines of code went from being treasured, reused, cared for and carefully curated, to being disposable and regenerable, practically overnight."

**Implicações:** se linhas de código se tornaram descartáveis e regeneráveis, o valor de engenheiros não está em produzir mais código por hora. Está em **arquitetar sistemas** que sobrevivam à entropia natural de bases que crescem mais rápido. Mais código = mais superfície pra falhar, mais testes, mais debugging, mais incident response. AI gera código instantaneamente; **engenheiros humanos** decidem o que deveria existir e o que pode ser removido.

**Tese central de Majors (reconhecida em todo o setor):** AI **aumenta** a necessidade de disciplina de engenharia, não diminui. Porque torna **fácil** fazer a coisa errada em escala. Sem CI/CD rigoroso, code review, observability, e refatoração disciplinada, empresas acumulam débito técnico exponencialmente mais rápido.

**Por que isso importa pra Ramon (e qualquer developer/builder com AI):**

- Tratar código gerado por AI como "rascunho descartável" sem review é o caminho mais rápido pro desastre.
- Discipline não é opcional — é a única defesa contra a gravidade de bases de código em expansão.
- Ferramentas como [[Datasette]] (do próprio Willison) são bons exemplos de projeto disciplinado: testes, releases pequenas, foco em simplicidade.

## Notas e Conexões

- Charity Majors é autora de _Observability Engineering_ (com Honeycomb co-founder) — texto fundamental sobre o tema.
- Conecta com [[Tim Challies - Technology is Fast, Sanctification Is Slow]] (mesma interseção AI + necessidade de processo humano lento) e com [[What Actually Happens When Your Team Adopts AI]] (reskilling, não cutting).
- Conexão teológica incidental: o "disposable and regenerable" contrasta com a tradição cristã de **cuidar** da criação (incluindo código) como stewardship, não como commodity descartável.
