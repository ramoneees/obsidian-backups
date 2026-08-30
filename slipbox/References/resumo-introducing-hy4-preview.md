---
title: "Introducing Hy4 Preview"
source: https://simonwillison.net/2026/Aug/29/hy4/
date: 2026-08-30
tags: [ia, llms, modelos-abertos, china]
---

# Introducing Hy4 Preview — Simon Willison

A Tencent entrou de vez na briga dos pesos abertos: lançou o Hy4 Preview, LLM somente texto com 770B de parâmetros totais, 49B ativos (MoE), janela de contexto de 1 milhão de tokens e 1,56 TB no Hugging Face. É um salto agressivo sobre o próprio Hy3 de julho (295B totais, 21B ativos, 256k de contexto, 598 GB) — em menos de dois meses, a empresa dobrou o tamanho e quadruplicou o contexto.

Willison, em vez de benchmarks, faz o que faz de melhor: abre o `chat_template.jinja` do modelo para entender o que ele realmente oferece. Descoberta: o Hy4 tem apenas dois níveis de raciocínio — `high` (padrão) e `no_think`. Sem meio-termo, e com exceções explícitas para valores inválidos — sinal de engenharia deliberada, não de descuido.

O clássico teste do "pelicano de bicicleta" passa, e o rastro de raciocínio revela um detalhe fascinante: o modelo delibera em inglês telegráfico ("Maybe add sunglasses? no."), sugerindo que gramática perfeita não é útil nem eficiente em tokens para texto de raciocínio oculto.

O sinal maior: a corrida chinesa de modelos abertos (Qwen, DeepSeek, agora Tencent Hy) não desacelera — e cada release estreita a distância para os laboratórios fechados do Ocidente.

## Por que importa

- A estratégia do Ramon (Qwen local para o privado, GLM cloud para o pesado) vive exatamente dessa corrida — Hy4 confirma que a fronteira de pesos abertos continua avançando em ritmo mensal.
- 1M de contexto + MoE de 49B ativos muda a matemática de servir modelos grandes com infra própria: o custo real é dos parâmetros ativos, não dos totais.
- Ler chat templates como método de avaliação é barato, rápido e negligenciado — técnica que vale copiar antes de confiar em qualquer benchmark de terceiros.

## Frases notáveis

> "New open weight text input (no vision) LLM from Chinese company Tencent today: 770B total parameters, 49B active parameters, 1M token context window, 1.56TB on Hugging Face."

> "It's interesting how the reasoning trace uses slightly truncated English, presumably because perfect grammar isn't useful or token efficient for hidden reasoning text."
