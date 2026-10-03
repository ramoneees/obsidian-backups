---
title: "Bluesky reply bot checker"
source: Simon Willison
date: 2026-09-30
url: https://simonwillison.net/2026/Sep/27/bluesky-bot-check/
author: Simon Willison
category: Tool
tags: [bluesky, reply-bots, vibe-coding, opus-5.5, api, ai-misuse]
ingested: 2026-10-03
---

# Bluesky reply bot checker

**Fonte**: Simon Willison (Simon Willison)
**Data**: 2026-09-30 . **URL**: https://simonwillison.net/2026/Sep/27/bluesky-bot-check/

## Resumo

Ferramenta de Simon Willison (vibe-coded com o Opus 5.5) que analisa um perfil do Bluesky em busca de padrões típicos de reply bots automatizados: velocidade de digitação, horários de publicação, padrões de engagement e outros sinais comportamentais, exibindo todas as medidas e regras para que se possa verificar o raciocínio. Motivação: os reply bots que o atormentam no Twitter começaram a aparecer no Bluesky — que, ao contrário do Twitter, ainda tem uma API livre e útil, o que torna a investigação viável.

## Ideias principais

- **Sinais heurísticos de bot**: respostas postadas segundos após outros posts da mesma conta, contas que nunca publicam conteúdo próprio (imagens/links) e respondem consistentemente a utilizadores com mais seguidores; interrogações também contam — Simon é "extra infuriated" por bots que o levam a responder perguntas que nenhum humano fez.
- **Transparência por desenho**: a ferramenta mostra cada medição e regra, com exemplos das replies que dispararam mais sinais, em vez de um veredicto opaco.

## Notas e conexoes

[[slipbox/References]]
