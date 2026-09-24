---
source: "Simon Willison"
title: "Shadow roots, explained with live examples"
date: 2026-09-23
url: https://simonwillison.net/2026/Sep/23/shadow-roots/
author: "Simon Willison"
category: "Tool"
tags: [css, shadow-dom, ferramentas, llm-gerado]
ingested: 2026-09-24
---

# Shadow roots, explained with live examples

**Fonte:** Simon Willison's Weblog (beat)
**Data:** 23 de setembro de 2026
**URL:** https://simonwillison.net/2026/Sep/23/shadow-roots/

## Resumo

Simon publicou uma ferramenta interativa em `tools.simonwillison.net/shadow-roots` que explica Shadow DOM/exemplos ao vivo: encapsulamento de estilo, herança, `slots`, `parts` e acesso via JavaScript — como shadow roots criam árvores DOM isoladas com stylesheets privadas que interagem com o DOM da página de formas controladas.

Detalhe metodológico: o beat é gerado a partir de um prompt — "Build an artifact to explain shadow roots in CSS with interactive examples" — rodado em **Fable 5.1 Medium**. Mais um datapoint da série dele de ferramentas explicativas construídas por LLM.

## Notas e conexões

- Útil diretamente para o trabalho de UI no cockpit (shadcn) quando precisar de encapsulamento de estilo em web components ou embeds.
- O pattern "pedir um artifact explicativo interativo a um modelo forte e publicar como ferramenta" é replicável para aprender qualquer tópico front-end — mesmo formato das notas [[Simon Willison-MCP was always a bad idea]] como opinião vs. aqui como tool.
