---
title: "NESFormer: um emulador de NES rodando dentro dos pesos do Qwen3.5"
source: https://simonwillison.net/2026/Oct/30/nesformer/
date: 2026-10-31
tags: [ia, llm, qwen, emulacao]
---

Drew Breunig, inspirado no projeto "qwenputer" de Divyansh Agrawal, colocou um emulador funcional da CPU 6502 do Nintendo Entertainment System dentro dos pesos do Qwen3.5-4B. O resultado dá para rodar ROMs reais — Super Mario Bros incluso — dentro do modelo de linguagem. Devagar demais para diversão alheia, mas funcional, com um CLI que aponta para os pesos e a ROM.

O processo é tão interessante quanto o resultado. Breunig usou o Opus 5.5 para explorar se dava para emular chip e RAM como se faz com FPGA, e o agente encontrou uma suíte de testes de conformidade da CPU do NES publicada há 15 anos por Christopher Pow (nes-test-roms). Ou seja: engenharia séria validada por testes de hardware de 2011 rodando dentro de pesos de transformer de 2026.

A provocação implícita: pesos de LLM são um substrato computacional mais arbitrário do que se imaginava. Se um 6502 cabe ali, a pergunta deixa de ser "o que um LLM sabe" e vira "o que cabe num LLM". O espírito era explícito: "just for fun, tudo bem se não for rápido" — ciência de brinquedo com seriedade de engenharia.

## Por que importa

- Cruzamento raro de ML com retrocomputing — e o loop "agente encontra suíte de testes de conformidade antiga e valida a coisa maluca" é exatamente o padrão de engenharia que você respeita.
- É o seu modelo privado (Qwen) sendo empurrado a um limite absurdamente criativo pela comunidade — bom termômetro de até onde a arquitetura vai.
- Pergunta em aberto que rende: se pesos carregam uma máquina inteira, onde está o limite entre modelo de linguagem e máquina universal?

## Frases notáveis

> "You can now play NES ROMs such as Super Mario Bros (very slowly) running inside Qwen!" — Simon Willison

> "I think we should build it! Just for fun. It's okay if it's not fast. We want to be able to have the weights, and a cli to run them that we can point at a ROM." — prompt de Drew Breunig ao Opus 5.5
