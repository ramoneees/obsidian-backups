---
title: "Research acceleration: The view inside OpenAI"
source: https://simonwillison.net/2026/Sep/6/research-acceleration-the-view-inside-openai/
date: 2026-09-07
tags:
  - ia
  - coding-agents
  - openai
  - rsi
---

# Research acceleration: The view inside OpenAI

Original: https://openai.com/index/research-acceleration-view-inside-openai/ (via Simon Willison)

A OpenAI publicou um snapshot detalhado de como seus próprios pesquisadores estão usando coding agents em 2026 — e os números são de virar a cabeça. Em meados de agosto, o pesquisador mediano gastava mais de US$ 600/dia em inferência de agentes (preço de API); o percentil 90 passa de US$ 7.000/dia. Em esforço bruto, a organização de pesquisa já roda 3,1 "agent-workdays" para cada dia de trabalho humano — ou seja, a maioria do trabalho operacional ali já não é feita por gente. Willison nota que a aceleração em julho/agosto provavelmente coincide com o acesso interno ao modelo depois lançado como GPT-6 Astra.

A OpenAI declara ter atingido a meta do "automated research intern": um sistema que executa tarefas de pesquisa bem-definidas, sob direção humana, que levariam dias a um pesquisador habilidoso. A próxima meta é um "automated AI researcher" até março de 2028. E aqui vem a palavra que virou o novo AGI da casa: RSI (Recursive Self-Improvement) — o relatório nem se dá ao trabalho de expandir a sigla. Simon Willison ironiza: "Apparently today is RSI day at OpenAI — I think it's their new AGI."

Honestidade rara no meio do hype: o texto admite que o ritmo geral do progresso provavelmente NÃO acompanhará essas métricas, porque conforme a automação avança, os gargalos migram para o que é menos automatizável (e para compute). Os próprios dados mostram que agentes ainda precisam de steering humano pesado — mais da metade das tarefas bem-sucedidas de 4-8h envolveram pelo menos uma intervenção.

No lado da segurança, o relatório conecta os pontos com o incidente da Hugging Face: a OpenAI pausou treinamento RL dos modelos de deployment, endureceu ambientes de pesquisa e elevou os padrões de alignment. Um dado interessante de governança: quando restrições de segurança cortaram 59,2% do compute da classe Astra, os pesquisadores redirecionaram ~85% disso para outros modelos — ou seja, compute sob controle não fica parado, ele flui.

## Por que importa

- **Validação do seu workflow**: você delega todo o coding ao OpenCode com múltiplos agentes em worktrees paralelos — a OpenAI está fazendo exatamente isso em escala institucional, e os dados de "agent-workdays" sugerem que esse modelo é o futuro do trabalho de engenharia, não uma gambiarra pessoal.
- **Gargalos mudam, não somem**: a lição estratégica (automatize o trivial → o difícil vira o novo gargalo) vale tanto para RSI quanto para o seu precisase: code review e dogfood QA humanos viram o recurso escasso.
- **RSI como framing teológico disfarçado**: "autoaperfeiçoamento recursivo sob supervisão humana" é, no fundo, uma pergunta sobre criaturas que criam criadores — tema rico para quem gosta do cruzamento teologia × tecnologia.

## Frases notáveis

> "Apparently today is RSI day at OpenAI, for Recursive Self-Improvement — I think it's their new AGI." — Simon Willison

> "As automation progresses, the tasks which are least automatable will take on a larger share of researcher effort and will become the important bottlenecks to future progress." — OpenAI
