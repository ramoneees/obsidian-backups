---
title: "Introducing Mistral Large 4: Le chonk"
source: Simon Willison
date: 2026-10-06
url: https://simonwillison.net/2026/Oct/6/le-chonk/
author: Simon Willison
category: link post
tags: [ia, llm, mistral, lancamento, pesos-abertos, benchmark]
ingested: 2026-10-07
---

# Introducing Mistral Large 4: Le chonk

**Fonte**: Simon Willison (link post)
**Data**: 2026-10-06 . **URL**: https://simonwillison.net/2026/Oct/6/le-chonk/

> "Mistral are back in the game" — preview do Mistral Large 4: 1 trilhão de parâmetros, 49 bilhões ativos, treinado em 3.800 GPUs NVIDIA Grace Blackwell próprias.

## Resumo

A Mistral lança em preview o Mistral Large 4, disponível via API, com open weights prometidos para "o fim deste mês". Dois níveis de raciocínio apenas — "none" e "high". Nos pelicanos do Simon, o modo "high" desenha melhor usando menos tokens de saída que o "none" (2.717 vs 3.275). No Artificial Analysis marca 38, logo atrás do DeepSeek 4.1 Flash (552B) — salto enorme sobre o Mistral Large 3 de dezembro (nota 9 no AA). Veredito: não é classe Fable, mas voltou a ficar ~6 meses atrás da fronteira.

## Ideias principais

- **MoE gigante, ativo pequeno**: 1T totais / 49B ativos é o padrão de eficiência que domina os lançamentos — capacidade bruta alta com custo de inferência de modelo médio.
- **Open weights como cronograma, não promessa vaga**: data declarada ("fim do mês") para os pesos; o ciclo API-preview → open weights virou o playbook europeu.
- **Raciocínio binário e contraintuitivo**: "high" melhorou o resultado E gastou menos tokens que "none" — o nível de raciocínio não é monotônico em custo.
- **Benchmark como narrativa**: 9 → 38 no AA é a história da ressurreição; a distância de ~6 meses da fronteira é a métrica que importa para adoção pragmática.

## Notas e conexoes

- O plugin que já suporta o modelo: [[Simon Willison-llm-mistral 0.16]].
- O teste cômico com o modelo: [[Simon Willison-Mistral Large 4]] (armadillo em fishnet tights em Marte).
- [[slipbox/References]]
