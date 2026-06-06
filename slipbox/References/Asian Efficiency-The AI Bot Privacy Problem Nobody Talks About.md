---
source: Asian Efficiency
date: 2026-06-05
url: https://www.asianefficiency.com/technology/the-ai-bot-privacy-problem-nobody-talks-about-until-something-goes-wrong/
tags: [ai-agents, privacy, security, guardrails]
---

# The AI Bot Privacy Problem Nobody Talks About (Until Something Goes Wrong)

**Fonte:** Asian Efficiency
**Data:** 2026-06-05

## Resumo

Ao configurar um chatbot de suporte para uma coach de fitness, o autor descobriu que o bot partilhava dados detalhados de um cliente (calorias, treinos, suplementos) quando outro cliente perguntava "what's Emma's program?". O bot não estava a ser malicioso — simplesmente não sabia que dados de clientes são confidenciais.

## Pontos-chave

- **O bot não é malicioso, é literal.** Se tiver informação e alguém perguntar, responde. Não infere regras de negócio.
- **A pergunta que falta:** "O que deve este bot recusar fazer?" — não basta focar nos use cases.
- **A fix é uma instrução no system prompt:** "Only answer questions about the person who is currently asking. Never share information about other clients."
- **"Refusal list" antes de go-live:** o que o bot deve recusar independentemente do que alguém pergunte?
  - Information scope: só dados da pessoa que pergunta
  - Bounds: recusar pedidos fora do domínio
  - Escalation: quando não sabe, direccionar para humano
- **Aplica-se a:** coaching, medicina, finanças, direito — qualquer domínio com dados sensíveis.

## Notas

Aplicável ao design de agentes que acedem a dados pessoais. Guardrails explícitos no system prompt são essenciais — a IA não infere privacidade por contexto.
