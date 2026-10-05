---
title: "Qwen3.8 27B addition in words"
source: Simon Willison
date: 2026-10-04
url: https://simonwillison.net/2026/Oct/4/qwen38-addition-in-words/
author: Simon Willison
category: Post
tags: [llms, qwen, local-llms, matematica, raciocinio, dgx-spark]
ingested: 2026-10-05
---

# Qwen3.8 27B addition in words

**Fonte**: Simon Willison's Weblog
**Data**: 2026-10-04 . **URL**: https://simonwillison.net/2026/Oct/4/qwen38-addition-in-words/

> Beat inspirado num experimento de Colin Frasier (Bluesky): GPT-4o somando inteiros e devolvendo o resultado só em palavras — forçando o modelo a "calcular no texto", sem atalho de token numérico.

## Resumo

Willison repetiu o experimento em ambiente controlado no DGX Spark local, rodando Qwen3.8-27B-Q4_K_M.gguf via sessão Codex Remote (GPT-6 Astra): 30 tentativas por combinação com raciocínio desligado, e uma comparação pareada de 169 casos com raciocínio médio ligado.

## Ideias principais

- **Sem raciocínio, aritmética colapsa em números grandes**: 23,57% de acerto numérico geral caindo de 97,04% (operandos de 1–3 dígitos) para 6,44% (10–13 dígitos) — com 96,17% de conformidade de formato, ou seja: o modelo seguiu a instrução, só não sabe somar.
- **Raciocínio resolve quase tudo**: 167/169 acertos (98,8%) com reasoning médio. As traces mostram o modelo reexecutando a soma dígito a dígito com carries ("6 + 9 = 15, write 5, carry 1") — aritmética como processo textual explícito.
- **Método barato e replicável**: a pipeline inteira (colar screenshot de benchmark alheio + pedir o mesmo experimento num agente de código com acesso ao hardware local) é um exemplo de pesquisa de fim de semana com LLMs — e um benchmark honesto para quantizações locais.

## Notas e conexoes

- Parente próximo no vault: [[resumo-Qwen-38-27B-Simon-Willison]] (lançamento do modelo) e [[resumo-qwen38-flash-next]] (a linha MoE que antecipa o Qwen4).
- Relevância local: 27B Q4 é exatamente a classe de modelo que roda no Mac (e o Mini de 16GB não segura essa classe — ver memória de setup). Confirmado empiricamente: sem reasoning estendido, não confiar em 27B local para qualquer conta que importe.

[[slipbox/References]]
