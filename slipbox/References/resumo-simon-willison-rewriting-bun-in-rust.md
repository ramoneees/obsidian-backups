---
title: "Rewriting Bun in Rust"
source: https://simonwillison.net/2026/Jul/8/rewriting-bun-in-rust/
date: 2026-07-09
tags: [engenharia-de-software, ia, agentic-engineering, devops]
blog: Simon Willison
author: Jarred Sumner (post original) / Simon Willison (link blog)
---

## Resumo

Willison comenta o post que Jarred Sumner (criador do Bun) prometeu desde maio: a reescrita completa do runtime do Bun de Zig para Rust. A peça é menos sobre linguagem e mais sobre o que **coding agents de fronteira tornam possível** — algo que a velha sabedoria de Joel Spolsky ("Things You Should Never Do, Part I", 2000) considerava suicídio técnico: parar tudo, jogar fora uma base, reescrever do zero.

A escolha por Rust não é estética — vem dos bugs. A lista de defeitos do Bun era dominada por use-after-free, double-free e "esqueceu de liberar num error path". Em Rust seguro, isso vira erro de compilador com cleanup automático via `Drop`. Misturar GC com memória manual (como Bun fazia em Zig) é território raro que nenhuma linguagem desenha bem.

O **fator habilitador** foi a test suite do Bun estar escrita em TypeScript — virou conformance suite. Um harness de agentes portou o código inicialmente como experimento, e em poucos dias a maioria dos testes passava. O PR final tem **+1 milhão de linhas**. Sumner monitorou workflows por 11 dias lendo outputs e pedindo ao Claude para editar o próprio loop quando algo quebrava. Princípio chave: quando algo dá errado, conserta o **processo que gera o código**, não o código.

O custo reportado é honesto: **5,9 bilhões de input tokens sem cache, 690 milhões de output, 72 bilhões de cached reads — cerca de US$ 165.000 em preço de API**. Bénção de trabalhar na Anthropic: tokens são por conta da casa. A nova implementação está em produção desde Claude Code v2.1.181 (17 junho 2026) — startup 10% mais rápido no Linux e ninguém notou. Boring is good.

## Por que importa

- É o **case study público mais transparente** de agentic engineering em larga escala: tem o custo ($165K), o método (conformance suite + adversarial review + consertar o processo, não o código) e o resultado (+1M linhas, PR mergeado, em produção há semanas). Excelente referência pra qualquer conversa sobre "será que dá pra delegar um rewrite a agentes?".
- Para quem trabalha com devops/infra, o insight prático é claro: **language-independent test suite é a pré-condição** que torna esse tipo de operação viável. Sem conformance suite escrita fora da linguagem alvo, agentes não conseguem verificar a si mesmos.
- Espelha uma virada de paradigma: a decisão de linguagem de programação deixou de ser one-way para projetos grandes. Coding agents de fronteira mudam o cálculo de Spolsky. Vale guardar essa peça ao lado de discussões sobre rewrites técnicos no slip-box.

## Frases notáveis

> "How do you review a PR with +1 million lines added? How do you start to build the confidence needed to responsibly merge large quantities of LLM-authored code? A language-independent test suite with a million assertions, adversarial code review and when something does go wrong, fixing the process that generates the code instead of hand-fixing the code."

> "Until very recently, programming language choice was a one-way decision for a project like Bun." — Jarred Sumner
