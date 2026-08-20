---
title: "smolmachines / smolvm como sandbox para Python e JavaScript não confiáveis"
source: https://simonwillison.net/2026/Aug/19/smolmachines-untrusted-sandbox/
date: 2026-08-20
tags: [ia, devops, sandboxing, llms]
---

## Resumo

Willison testou o smolvm 1.8.3 (smolmachines.com) como sandbox para execução de código não confiável — transforms de dados em Python e JavaScript escritos por usuários. O veredito: bem adequado. As VMs usam isolamento por hardware (microVMs estilo Firecracker) em vez de containers com kernel compartilhado, o que é uma fronteira de segurança mais forte por padrão.

A bateria de testes cobriu tudo que importa em produção: imagens locais offline, execução sem rede, limites de CPU/RAM, timeouts enforcement no guest, quotas de armazenamento, mounts de input read-only e output writable, e modo `--unprivileged`. Tudo funcionou como esperado. Cold start entre 0,6–1,5s; execuções a quente em ~50ms — números que viabilizam uso em pipelines de dados reais.

O detalhe mais interessante é meta: o agente (Claude Fable 5 no Claude Code for web) descobriu que seu próprio ambiente não tinha `/dev/kvm` (sem virtualização aninhada), e resolveu sozinho rodar toda a bateria de testes num runner do GitHub Actions — criando o workflow, executando, coletando logs e removendo-o no commit final. Willison chama isso de mais um exemplo do Fable ser "relentlessly proactive".

## Por que importa

- **Isolamento por hardware > containers compartilhados.** Para qualquer pipeline que execute código gerado por LLM ou fornecido por usuários, microVMs são a fronteira correta — Willison valida que isso já é prático, com latência de dezenas de ms.
- **Agente que contorna limitações do próprio ambiente.** O Plano B autônomo (GitHub Actions como ambiente de teste) é um padrão de orquestração que agentes de DevOps vão repetir — vale ter no radar de automação.
- **"Executar código não confiável" é o problema central da era de coding agents.** Sandbox rápido + barato + offline muda o custo de delegation de tarefas a agentes.

## Frases notáveis

> "Testing smolvm 1.8.3 shows it is well suited for sandboxing untrusted Python and JavaScript data transformations using hardware-isolated VMs rather than shared-kernel containers."

> "Plan B: GitHub Actions ubuntu runners DO expose /dev/kvm → run the real test battery via a temporary workflow on this branch, collect logs, remove workflow in final commit."
