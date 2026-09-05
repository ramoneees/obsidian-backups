---
title: "The Pelican comparison grid for Astra is pretty interesting"
source: https://simonwillison.net/2026/Sep/4/astra-pelicans/
date: 2026-09-05
tags: [ai, openai, gpt-6-astra, llm-benchmarks]
---

Willison recebeu acesso ao GPT-6 Astra e fez o que sempre faz: gerou SVGs de pelicanos andando de bicicleta em cinco níveis de raciocínio (low, medium, high, xhigh, max — Astra não suporta reasoning=none) e montou uma grade comparativa com os GPT-5.6 Sol, Terra e Luna. Resultado: além de divertido, empiricamente útil.

Os achados: (1) os pelicanos do Astra são muito melhores — até o nível low do Astra supera qualquer GPT-5.6 em qualquer nível; (2) Astra abaixo de max ainda não acerta as pernas do pelicano nos dois lados do quadro; (3) o Astra custa ~2x o Sol ($10/$50 por milhão de tokens vs $5/$30), mas consome bem menos tokens por geração — um pelicano Astra low sai por 9,55 centavos, contra 10 centavos por resultados muito piores nos outros modelos; (4) detalhe forense: Astra e Luna usaram 16 tokens de entrada, Sol e Terra usaram 26.

A conclusão provocativa fica na última linha: "Eu me pergunto se Astra e Luna são mais relacionados entre si do que a OpenAI admite?" — ou seja, o contador de tokens do prompt vira impressão digital do tokenizer/pipeline interno, e o benchmark brincalhão do pelicano funciona como ferramenta de análise competitiva.

É mais um episódio da série pelican-riding-a-bicycle, o micro-benchmark qualitativo que Willison criou porque SVG força o modelo a traduzir uma imagem mental em coordenadas geométricas coerentes — algo que benchmarks numéricos não capturam.

## Por que importa
- Metodologia barata de avaliação de modelos que Ramon pode copiar: um prompt visual único + grade lado a lado + custo por geração revela mais que benchmarks autorreportados (complementa o resumo anterior do lançamento do Astra, que mostrou os números contestáveis do ARC-AGI 3).
- O dado de custo é acionável: se Astra low supera Sol max por menos dinheiro, a escolha de modelo para tarefas de imagem/código SVG muda — relevante para os roteamentos de modelo do próprio setup Hermes (GLM para pesado, Qwen para privado).
- O "fingerprint" de 16 vs 26 tokens de entrada é um lembrete de que metadados triviais vazam arquitetura interna — mesmo instinto forense do caso dos rogue agents.

## Frases notáveis
> "Astra low produces a better pelican than ANY of the GPT-5.6 Sol models at any level, for 9.55 cents. Spending 10 cents on any other model gets a much worse result."

> "I wonder if Astra and Luna are more related to each other than OpenAI let on?"
