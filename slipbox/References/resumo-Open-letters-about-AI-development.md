---
title: "Open letters about AI development"
source: https://simonwillison.net/2026/Aug/2/open-letters/
date: 2026-08-02
tags: [ia, governanca, open-source, open-weights, llms]
author: Simon Willison
---

## Resumo

Simon Willison resume duas cartas abertas publicadas em julho de 2026 que polarizam o debate sobre o futuro dos modelos abertos. A primeira, **"Open Weights and American AI Leadership"** (24/jul), coordenada pela Microsoft, reúne 235 signatários — NVIDIA, Amazon, Y Combinator, Linux Foundation e OpenAI — em defesa dos modelos *open-weight* como contraponto a qualquer ímpeto do governo americano de bani-los. A peça central do argumento: modelos fechados são "single points of failure" e a comunidade aberta tem mais capacidade de auditar vulnerabilidades. A carta também legitimiza explicitamente a destilação como técnica válida de treinamento.

A segunda carta, **"Pacing the Frontier"** (28/jul), reúne 1.324 funcionários de empresas de fronteira (incluindo Ilya Sutskever, Dario Amodei, Jakub Pachocki) com um pedido oposto: que o governo americano apoie um esforço internacional para **deliberadamente desacelerar** o desenvolvimento de IA. O medo é concreto — Anthropic já produz 80% do seu código com Claude Code, OpenAI reduziu custos de serving em 20% com Sol, e a Kimi projetou um chip com seu próprio modelo nano. A automação da própria pesquisa em IA deixou de ser hipótese.

A Anthropic publicou sua própria resposta três dias depois, rejeitando banimento total mas pedindo ação contra "operações industriais de destilação" — uma fricção explícita com o restante do setor.

## Por que importa

- Captura o eixo tenso do momento em IA/ML: a comunidade *open-source* contra o *safety-establishment* — ambas com argumentos legítimos. Para quem trabalha com IA, é o mapa do campo de batalha regulatório dos próximos anos.
- Os números concretos (80% do código Anthropic escrito por Claude, 20% de redução de custo via agentes) são evidência rara de automação autocatalítica em produção. Vale guardar para referência em argumentos sobre trajetória de progresso.
- Toca diretamente em devops/automação: a fronteira entre "ferramenta" e "colaborador autônomo" está sendo cruzada dentro das próprias empresas que constroem a tecnologia — relevante para qualquer um que esteja desenhando pipelines de IA.

## Frases notáveis

> "Relying solely on closed models is not inherently safe: they can be breached, misused, or fail in ways that outsiders cannot detect."

> "We request that the U.S. government support an international effort to develop the technical and governance tools needed to deliberately pace the frontier of automated AI development."
