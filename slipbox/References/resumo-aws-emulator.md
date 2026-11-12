---
title: "aws-emulator"
source: "https://simonwillison.net/2026/Nov/11/aws-emulator/"
date: 2026-11-12
tags: [devops, aws, testing, agentic-engineering]
---

A AWS finalmente lançou um emulador oficial para rodar testes contra um clone local dos serviços deles — a resposta canônica ao LocalStack, agora vinda de dentro de casa. Fim da era de precisar de API key paga (e de conta com quota) só para rodar suite de testes.

O detalhe que virou manchete: o emulador é escrito em Rust por um enxame de agentes — 29.684 commits nas três primeiras semanas do projeto. O Swami Sivasubramanian escreveu um post no blog do Werner Vogels sobre como o projeto aconteceu, com o subtítulo que já é um manifesto: qual é o trabalho do engenheiro quando os agentes escrevem o código.

Ainda exige Docker no macOS e Windows, o que Willison critica com razão — o sonho é um binário único que entra direto na suite de testes padrão, em qualquer linguagem, sem a camada de container.

Para quem vive de infra local (OrbStack, k3s, arrays de containers), a pergunta prática é simples: quanto do boilerplate de mock de SDK da AWS isso mata? Se o emulador for fiel, tests de integração contra S3/SQS/Lambda deixam de ser teatro e viram infraestrutura padrão — sem custo, sem flakiness de rede.

## Por que importa

- Devops puro: teste local contra AWS sem custo nem mocks artesanais — impacto direto em CI (GitHub Actions/Gitea) e no tempo de setup de projetos.
- É um caso de estudo de agentic engineering em escala industrial: 30 mil commits em 3 semanas, com humanos orquestrando. Comparável ao que você roda com OpenCode/herdr, só que na AWS.
- O post do Vogels/Swami sobre "o trabalho do engenheiro quando agentes escrevem o código" é leitura obrigatória pra quem delega coding a agentes — que é exatamente o seu fluxo.

## Frases notáveis

> "It's written in Rust by a huge swarm of agents - 29,684 commits in the first three weeks of the project."

> "Finally, an official emulator from AWS to run tests against a local clone of their many different services without having to provision a paid API key to do so."
