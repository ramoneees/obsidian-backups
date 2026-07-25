---
title: 'Introducing Claude Opus 5'
source: https://simonwillison.net/2026/Jul/24/introducing-claude-opus-5/
date: 2026-07-25
tags: [ia, llm, anthropic, claude, agi]
---

## Resumo

Simon Willison comenta o lançamento do Claude Opus 5 (Anthropic, 24/07/2026) com base no anúncio oficial — ele próprio estava offline caiaquando com lontras-marinhas quando saiu o release. O Opus 5 está no topo do Artificial Analysis leaderboard, à frente inclusive do Claude Fable 5, mas a um preço que a Anthropic descreve como "metade do preço" para chegar perto da fronteira de inteligência do Fable 5. O preço nominal é o mesmo do Opus 4.8, e mantém o "fast mode" ao dobro do custo da base.

O ponto que Willison destaca é o salto de proatividade. Em uma tarefa do Frontier-Bench, Opus 5 recebeu o desenho de uma peça mecânica sem acesso direto ao arquivo de imagem — e em vez de falhar, escreveu por conta própria um pipeline de visão computacional para extrair a geometria dos pixels brutos e reconstruir a peça em FreeCAD 3D. Para Willison, isso confirma o padrão que ele chamou de "relentlessly proactive" no Fable.

Há também um sinal político relevante: a Anthropic deliberadamente **não** treinou Opus 5 em tarefas cibernéticas ofensivas, mesmo sabendo que o modelo, ao ficar mais capaz, melhorou naturalmente em encontrar vulnerabilidades. A intenção declarada é manter distância da Mythos 5, que permanece à frente em *explotação*. Willison fecha com uma piada seca: "Hopefully this means the US government won't shut it down!"

## Por que importa

- **Estado da fronteira LLM em 2026**: o lançamento documenta a dinâmica Anthropic↔OpenAI/Google em tempo real — Opus 5 versus Fable 5 versus Mythos 5 dá um mapa claro de quem compete em quê.
- **Proatividade como nova fronteira**: o episódio do pipeline de visão computacional auto-escrito é caso de manual sobre agenticidade emergente. Vale guardar como referência para pensar o que "agente" realmente significa além de buzzword.
- **Decisão de design ético-técnica**: a escolha de não treinar em cyber-ofensiva, mesmo sabendo que o modelo aprenderia sozinho, é um precedente importante sobre onde ficam os limites deliberados em segurança de IA.

## Frases notáveis

> "On one Frontier-Bench task, Opus 5 was given a drawing of a machine part and asked to write code to rebuild it as a 3D FreeCAD model. However, in this task, the model was intentionally given no way to directly view the drawing. Opus 5 responded by writing its own computer vision pipeline to pull the geometry from the raw pixels, then reconstructed the full machine part."

> "The model has nevertheless improved substantially on these tasks as a result of becoming more generally capable, and it comes close to Mythos 5 at *finding* cybersecurity vulnerabilities. However, it remains substantially behind Mythos 5 on the *exploitation* of those vulnerabilities."
