---
title: "Release: condense-json 1.0"
source: https://simonwillison.net/2026/Aug/2/condense-json/
date: 2026-08-03
tags: [python, llm, devops, otimizacao]
author: Simon Willison
---

## Resumo

Simon Willison anuncia a versão 1.0 de `condense-json`, uma biblioteca Python pequena e focada que resolve um problema específico de infraestrutura em pipelines de LLM: JSON grande e verboso sendo serializado em logs SQLite. A técnica é direta — recebe um JSON de entrada e um dicionário de substituições, e devolve o mesmo JSON com strings repetidas trocadas por referências `{"$r": ["prefixo", {"$": "id"}], "sufixo"}`. A função inversa `uncondense_json` restaura o original.

O ganho prático é economia de espaço em disco e banda quando o mesmo payload aparece em milhares de eventos de log gerados por agentes. Willison usa isso dentro do [LLM](https://llm.datasette.io/) (seu CLI para modelos), conforme o PR #1586. É o tipo de ferramenta que parece trivial até você operar em escala e descobrir que 70% do seu log é a mesma string do system prompt repetida.

A nota de rodapé do post é a mais willisoniana possível: ele está tentando "ficar mais corajoso" para liberar versões 1.0 — um comentário sobre maturidade de software, semântica de versão e a tentação de deixar bibliotecas pessoais em 0.x indefinidamente.

## Por que importa

- É referência concreta para qualquer pipeline de logging de LLM que esteja sangrando espaço com prompts repetidos — útil para quem opera agentes 24/7.
- A abordagem de "substituição reversível" é uma técnica reutilizável em qualquer serialização que tenha alta redundância de strings (telemetria, traces, respostas cacheadas).
- Combina com a stack que Ramon provavelmente já considera: a mentalidade de "construir agentes" em vez de "alugar SaaS" do post da Asian Efficiency — só que aqui, em micro-escala.

## Frases notáveis

> "I'm trying to get braver at releasing 1.0 versions. This little library is a year and a half old now — I've applied some sensible and non-disruptive fixes and shipped the big 1.0 for it."

> "The idea is to make it easier to store JSON that includes duplicated data from other related structures."
