---
source: "Simon Willison"
title: "Jev introduces a new shape of LLM - System One, aka Decision Models"
date: 2026-09-21
url: https://simonwillison.net/2026/Sep/21/jev/
author: "Simon Willison"
category: "Blog"
tags: [ia, llms, machine-learning, arquitetura]
ingested: 2026-09-22
---

A TypeSafe AI lançou o Jev, primeiro de uma nova categoria que eles chamam de "modelos System One" — Willison prefere o nome "decision models", emprestado da Maggie Appleton. A forma é inusitada: entrada em texto como qualquer LLM, mas a saída não é texto — são números de ponto flutuante correspondendo a categorias, respostas sim/não, notas e scores de confiança. Em palavras deles: "estado não estruturado entra, decisões probabilísticas tipadas saem."

O modelo econômico é o provocador: cobram só o input (US$ 0,042/milhão de tokens — mais barato que o GPT-5 Nano) e o output é grátis. Faz sentido quando a saída é um float. Os casos de uso óbvios são classificação: detecção de spam, labeling, priorização, ranking — e reranking de busca (BM25 barato puxa 100 candidatos, o Jev pontua a relevância de cada um). Perguntas rodam em paralelo, então muitas perguntas custam o mesmo tempo que uma.

A segunda metade do artigo é a mais interessante: o "regresso à black box". LLMs já são caixas-pretas, mas pelo menos devolvem uma justificativa (ainda que não confiável). O Jev devolve só um número — se ele marcar algo como spam, não há como saber quais sinais pesaram. Willison aponta o risco óbvio de viés oculto (espera que ninguém use isso para ranquear candidatos a emprego) e conclui que evals e experimentos estruturados viram ainda mais críticos — sorte que o modelo é tão barato que rodar milhares de experimentos custa centavos.

## Por que importa

- Classificação é o tipo de tarefa mecânica que você já delega a modelos pequenos (qwen3.8-flash em crons) — o Jev propõe uma forma ainda mais barata e determinística para exatamente esse nicho, com distribuição de probabilidade em vez de texto para parsear.
- O caso de uso de reranking (BM25 + Jev) é receita pronta para busca no precisase — matching de voluntariado/doações é, no fundo, um problema de scoring.
- A crítica da black box é um lembrete teológico-disruptivo raro em tech: sistemas que decidem sem explicar exigem evals como disciplina ética, não só engenharia.

## Frases notáveis

> "Think of Jev as a frontier-intelligence function call: unstructured state in, typed probabilistic decisions out."

> "I really hope nobody uses Jev to rank job applicants—that floating point number could conceal all manner of unseen bias baked into the models, and experimentally picking that bias apart is going to be a tricky business."
