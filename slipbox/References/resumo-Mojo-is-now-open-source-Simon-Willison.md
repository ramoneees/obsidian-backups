---
title: "Mojo🔥 is now open source"
source: https://simonwillison.net/2026/Aug/18/mojo-is-now-open-source/
date: 2026-08-19
tags: [python, open-source, gpu, ml]
---

# Mojo🔥 is now open source

O Mojo, linguagem da Modular criada para programação de GPU de alta performance, finalmente cumpriu a promessa feita em maio de 2023: compilador e toolchain liberados sob licença Apache 2.0. O lançamento vem logo depois do Mojo 1.0, embarcado na semana passada.

A história tem uma reviravolta importante para quem acompanha Python de perto: o objetivo original era ser um *superset* de Python, permitindo reusar o ecossistema existente como bootstrap. Em agosto de 2025, a Modular mudou o discurso oficial: "Mojo pode ou não evoluir para um superset completo de Python, e tudo bem se não evoluir." A compatibilidade total saiu do centro do projeto.

O que sobrou é mais honesto e talvez mais útil: uma linguagem própria, otimizada para tornar a programação de GPU o menos dolorosa possível, com sintaxe *inspirada* em Python — mas sem compatibilidade de 100% com código existente. Curiosamente, a Modular aposta que ferramentas de codificação assistida por IA farão a migração de Python para Mojo ser mais suave do que seria otherwise.

Para Willison, link post curto e factual — mas o sinal importa: mais uma peça da infraestrutura de ML frontier deixando o mundo proprietário.

## Por que importa

- **Infra de ML abrindo**: compilador e toolchain de uma linguagem pensada para GPU/era-LLM sob Apache 2.0 é mais um deslocamento do centro de gravidade do ML para open source.
- **A Meta-mudança**: abandonar o "superset de Python" e assumir-se linguagem própria mostra como metas de compatibilidade cedem quando o alvo é performance em GPU. E a justativa oficial passa por *ferramentas de IA que migram código* — IA resolvendo o atrito que a decisão de design criou.

## Frases notáveis

> "Mojo may or may not evolve into a full superset of Python, and it's okay if it doesn't." (documento de visão da Modular)

> "Today Mojo is its own language, optimized to make GPU programming as painless as possible using syntax inspired by Python, if not 100% compatible with existing code."
