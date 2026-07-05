---
title: "Better Models: Worse Tools"
source: https://simonwillison.net/2026/Jul/4/better-models-worse-tools/
date: 2026-07-05
tags:
  - ia
  - llms
  - agentic-engineering
  - claude
---

## Resumo

Simon Willison linka para um post de Armin Ronacher (criador do Flask e do Pocoo) relatando um problema estranho no Pi, seu coding agent: as versões mais novas dos modelos Claude — Opus 4.8 e Sonnet 5 — estão ficando *piores*, não melhores, em chamar o tool de edição do Pi corretamente. Os modelos invocam a ferramenta com campos extras e inventados dentro do array `edits[]`, violando o schema. O tool call é rejeitado e o agente pede nova tentativa.

A ironia amarga é que modelos menores e antigos não têm esse problema. A hipótese de Armin é a seguinte: a Anthropic tem treinado intensivamente (provavelmente via Reinforcement Learning) os modelos recentes para usar *bem* os tools de edição que estão baked-in no Claude Code — search/replace str-based, conforme a documentação oficial. O resultado colateral é que harnesses de terceiros como o Pi, com schemas próprios de edição, sofrem um *downgrade* de performance. Cada vendor (Anthropic com search/replace, OpenAI com apply_patch) está treinando modelos para os próprios tools, criando ilhas de otimização.

Willison deixa no ar a pergunta incômoda: coding agents de terceiros precisarão implementar múltiplas variantes do tool de edição só para casar com o modelo que o usuário escolheu? É um problema clássico de dependência de fornecedor — mas aplicado à fronteira mais quente da IA em 2026.

## Por que importa

- Para o Ramon (devops + IA): documenta um risco operacional real em produção de agentes. Se você está construindo infra agentic em cima de APIs de frontier labs, o tool schema não é detalhe — é superfície de falha que muda silenciosamente entre versões de modelo.
- O caso é exemplo concreto de **vendor lock-in emergente**: o "melhor modelo" não é o melhor modelo *para você* se o seu harness divergir dos tools nativos do lab. Decisão arquitetural que precisa estar no radar.
- Conecta-se ao tema da curadoria de tools que o Ramon pratica no dia-a-dia (escolher entre CLI, frameworks, integrações). Vale a pena ler em diálogo com o artigo do Fable abaixo — onde Willison mostra que mesmo com o melhor modelo, revisão humana cruzada ainda pega bugs críticos.

## Frases notáveis

> "newer Claude models sometimes call Pi's edit tool with extra, invented fields in the nested `edits[]` array. And not Haiku or some small model: Opus 4.8."

> "the SOTA models of the family are worse at this specific tool schema than their older siblings."
