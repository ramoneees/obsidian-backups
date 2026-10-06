---
title: "pwasm 0.2a0 — um motor WebAssembly em Python puro, todo vibe-coded"
source: Simon Willison
url: https://simonwillison.net/2026/Oct/1/pwasm/
author: Simon Willison
category: python
date: 2026-10-06
tags: [ia, vibe-coding, python, webassembly]
ingested: 2026-10-06
---

Simon Willison retomou um dos seus "folly projects": pwasm, um motor WebAssembly escrito inteiramente em Python puro — e inteiramente vibe-coded, construído em janeiro durante o primeiro surto de "AI mania" do ano. O projeto ficou parado desde então.

A rotina de retomada é uma aula de delegação: ele soltou o Claude Opus 5.5 no repositório com um único prompt — avaliar o estado atual do pwasm, considerar o que levaria para rodar os experimentos de MicroPython e micro JavaScript do repositório de pesquisa sobre ele, e o que levaria para acelerá-lo.

Quarenta e dois commits depois, com follow-up mínimo, o resultado: o motor agora cobre quase toda a especificação WASM, e a wheel no PyPI vem com builds WASM funcionais de MicroPython, QuickJS e Micro QuickJS. Sim — Python rodando WebAssembly rodando Python e JavaScript. Recursão suficiente pra agradar qualquer um.

Ele mesmo avisa que não confia no resultado — por isso a tag alpha. O ponto provocativo do post é outro: modelos de hoje melhorando o trabalho de modelos de dez meses atrás. Uma codebase abandonada virou benchmark vivo do progresso da IA.

## Por que importa

- É o workflow do Ramon documentado por quem melhor escreve sobre LLMs: delegar o coding inteiro, agente em streak longa de commits, humano só no prompt inicial e no review.
- Vibe-coding como método legítimo, com honestidade sobre confiança: código que ninguém leu linha a linha, mas que compila, empacota e roda — com tag alpha assumida.
- Métrica nova de progresso em IA: nada de benchmark acadêmico — "modelo novo melhorando projeto de modelo velho" é uma medida concreta e replicável.

## Frases notáveis

> "I wouldn't trust this thing at all — hence the alpha version tag — but it's interesting seeing how today's models can improve on the work of models from 10 months ago."

> "Evaluate current state of pwasm - then consider what it would take to get the MicroPython and micro JavaScript experiments from the research repo working under it - and what it would take to speed it up"
