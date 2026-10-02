---
title: "Anthropic Frontier Red Team: GLM-5.3 and the Spread of Advanced Cyber Capabilities"
source: https://simonwillison.net/2026/Sep/29/anthropic-frontier-red-team/
date: 2026-10-02
tags: [ia, seguranca, agentes, glm]
---

# Anthropic Frontier Red Team: GLM-5.3 and the Spread of Advanced Cyber Capabilities

Simon Willison repostou um trecho do relatório do Frontier Red Team da Anthropic que merece leitura dupla por quem trabalha com agentes de código. No benchmark interno de Binary Exploitation (100 tarefas sorteadas), o **GLM-5.3 executou hijacks completos de control flow em 4% dos testes**; o Claude Mythos Preview, em 6%. Modelos da geração anterior — Claude Opus 4.6 e GLM-5.2 — não passaram em nenhuma. O ponto do relatório não é o ranking entre modelos: é que um limiar foi cruzado. Exploração binária autônoma, de ponta a ponta, saiu do impossível e entrou no catálogo de capacidades de modelos de fronteira.

A leitura provocativa para quem tem GLM-5.3 rodando como modelo pesado de código no OpenCode: o modelo que o Ramon usa diariamente para delegar implementação aparece num relatório de capacidades ciberofensivas. Não se trata de parar de usá-lo — trata-se de entender o que "modelo de fronteira em 2026" significa: a mesma capacidade que escreve código correto escreve exploits corretos. Utility e capability são a mesma moeda, só muda a intenção de quem gira.

A implicação prática é higiene de devops, não paranoia: sandbox em tudo que agente toca, permissões mínimas, e o hábito de tratar output de agente como código não-confiável até passar por revisão. O agente que domina control flow consegue, por definição, sequestrar um. A segurança de IA deixou de ser tema de laboratório para virar rotina de quem opera pipelines com modelos — exatamente o contexto do fluxo prometheus→momus→sisyphus, onde o momus (review) existe justamente para ser o humano no circuito.

Fonte em dois níveis: o post do Willison é formato citação, e o relatório completo está na Anthropic. Willison segue sendo o canário mais confiável para acompanhar pesquisa de segurança de modelos sem hype — ele apenas aponta o dado e deixa a implicação com o leitor.

## Por que importa

- O modelo citado é o mesmo que roda nas delegações de código do Ramon (OpenCode = glm-5.3): capacidade ofensiva e utilidade de coding vêm do mesmo lugar.
- Reforça com dado de benchmark a prática de sandbox + permissões mínimas + review obrigatório em agentes — o "momus" do board é o controle, não formalidade.
- Marca um marco de capacidade (primeira geração a passar em binary exploitation autônomo) que vale acompanhar no próximo ciclo de modelos.

## Frases notáveis

- "GLM-5.3 develops full control flow hijacks in 4% of the trials; Claude Mythos Preview did so in 6%."
- "a meaningful threshold has clearly been crossed: earlier models, like Claude Opus 4.6 and GLM-5.2, do not succeed in any of them."
