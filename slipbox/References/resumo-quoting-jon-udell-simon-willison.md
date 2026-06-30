---
title: "Quoting Jon Udell: 'Agent in the loop', not 'human in the loop'"
source: https://simonwillison.net/2026/Jun/28/jon-udell/
date: 2026-06-30
tags: [ia, coding-agents, devops, engenharia, simon-willison]
---

# Quoting Jon Udell: "Agent in the loop", not "human in the loop"

Post curto de Simon Willison (28 de junho de 2026) citando um parágrafo de Jon Udell que está circulando entre engenheiros: "Doctor, it hurts when agents create unreviewable PRs." "Don't do that." A frase capta uma crise emergente no desenvolvimento assistido por IA — Pull Requests gerados por agentes com milhares de linhas adicionadas/alteradas que humanos não conseguem revisar de ponta a ponta.

## A virada narrativa

Udell recusa o slogan "human in the loop" porque ele cede autoridade às máquinas. Propõe o inverso: "agent in the loop". O loop é nosso, sempre foi, sempre será. Agentes são recrutados para entrar num processo humano existente — não o contrário. A diferença é mais semântica do que parece: no primeiro modelo, humanos supervisionam outputs de máquina; no segundo, humanos dirigem e agentes contribuem num fluxo legível, testável, revisável. Um processo assistido por agente não precisa ser caixa-preta que recebe prompt e cospe feature.

## A prática no Bram

A carne do post original de Udell é o Bram, um app desktop em Tauri (Rust) que ele está bootstrapping com Claude Code e Codex. Detalhe notável: Udell nunca escreveu uma linha de Rust, mas lê cada linha que os agentes produzem conforme eles escrevem, e empurra de volta quando algo não cheira bem. A workflow força granularidade — tarefas pequenas, testáveis, registradas numa worklist local que serve de contexto compartilhado entre humano e agentes (e entre agentes diferentes). É uma tentativa concreta de operacionalizar "agentic engineering" sem cair no anti-padrão do PR inauditável.

## Por que importa

- O contraste "human in the loop" vs "agent in the loop" é uma das formulações mais nítidas disponíveis sobre como organizar times com IA. Aplica diretamente a qualquer setup de devops/automação que o Ramon esteja construindo com coding agents (Claude Code, Codex, etc.) — puxa a discussão de "como eu reviso isso" para "como eu organizo o trabalho de modo que revisão seja possível".
- O Bram-workflow (worklist local + chunks pequenos + contexto compartilhado entre agentes) é um padrão replicável: ele resolve o problema do contexto que vaza a cada nova sessão, e ainda permite trocar de agente (Claude ↔ Codex) sem perder o fio. Vale como referência para o setup do Ramon.
- O artigo se entrelaça com teologia de modo útil, embora discreto: "agent in the loop" lembra a doutrina da providência — Deus sustenta o loop da história e nos chama a agir dentro dele, não a entregar o leme. É o tipo de cruzamento tecnologia/teologia que o Ramon curte.

## Frases notáveis

> "I dislike the phrase 'human in the loop' because it cedes authority to the machines. Let's flip the narrative. It's our loop, we work the same way we always have, now we recruit agents to join the team."

> "An agent-assisted process need not be a black box that takes in prompts and emits features."
