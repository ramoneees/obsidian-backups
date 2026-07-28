---
title: "An opinionated guide to which AI to use to do stuff"
source: "Simon Willison's Weblog (link blog sobre Ethan Mollick)"
url: "https://simonwillison.net/2026/Jul/27/an-opinionated-guide-to-which-ai-to-use-to-do-stuff/"
author: "Simon Willison (sobre guia de Ethan Mollick, One Useful Thing)"
date: 2026-07-28
tags: [ia, llms, agentes, devops, automacao, escolha-de-ferramentas, ethereum-mollick]
category: ia-pratica
ingested: 2026-07-28
blogwatcher_id: 1235
---

# An opinionated guide to which AI to use to do stuff

**Fonte:** Simon Willison's Weblog (link blog sobre o guia de Ethan Mollick na *One Useful Thing*)
**Data original:** 27 de julho de 2026
**URL:** https://simonwillison.net/2026/Jul/27/an-opinionated-guide-to-which-ai-to-use-to-do-stuff/

## Resumo

Simon Willison comenta a evolução do guia de Ethan Mollick para escolher qual IA usar em 2026. Há um ano, a recomendação era centrada em chat — ChatGPT, Claude, Gemini — com Deep Research como modo alternativo. Hoje, a ênfase mudou para "sistemas agênticos", onde a IA entrega o equivalente a várias horas de trabalho humano em uma única execução.

Willison nota que o Gemini caiu da lista de Mollick porque o Google ainda não tem entrada consolidada na categoria Codex/ChatGPT Work/Cowork — o Gemini Spark ainda não se provou. O ponto central é didático: existem hoje múltiplas formas de "dar um computador" para a IA usar, e os nomes não mapeiam entre si (ChatGPT Work ≠ Codex; Claude Cowork ≠ Code).

O insight mais provocativo: quando você troca o app móvel do ChatGPT de "Chat" para "Work", a versão roda o Code Interpreter container sem restrição de acesso à internet. Isso muda completamente o que se pode fazer com a ferramenta no celular. Willison critica abertamente a UX dessa sobreposição de modos como "espetacularmente unintuitiva".

O link post funciona como instantâneo do estado-de-arte para 2026: a fronteira não está mais em qual modelo é melhor em benchmarks, mas em qual produto te dá um agente capaz de realmente trabalhar no seu computador por horas.

## Por que importa

- Para devs e entusiastas de IA/ML, é mapa de leitura rápida do ecossistema agêntico atual (Codex, Claude Code, Cowork, ChatGPT Work) — útil para escolher a stack antes de mergulhar em uma ferramenta nova.
- A crítica de UX do Willison é lição para quem constrói ferramentas: dar poder real a agentes exige pensar cuidadosamente em como expor essa capacidade ao usuário sem que a configuração fique invisível.
- A mudança de "qual modelo responder melhor" para "qual sistema entrega mais trabalho útil" é uma virada filosófica sobre o que esperamos de IA — conecta com o perfil de quem pensa em automação e devops como amplificadores de capacidade, não como substitutos de respostas.

## Frases notáveis

> "The most powerful way to use AI is to give it access to your computer."

> "I think the difference between ChatGPT Work on a mobile device and ChatGPT Work inside the desktop app (where it's effectively a less intimidating skin on top of Codex) is spectacularly unintuitive."
