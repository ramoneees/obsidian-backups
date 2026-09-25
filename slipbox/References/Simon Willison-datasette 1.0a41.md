---
source: "Simon Willison"
title: "datasette 1.0a41"
date: 2026-09-24
url: https://simonwillison.net/2026/Sep/24/datasette/
author: "Simon Willison"
category: "Release"
tags: [datasette, javascript, web-components, opentelemetry]
ingested: 2026-09-25
---

# datasette 1.0a41

**Fonte:** Simon Willison (weblog)
**Data:** 24 de setembro de 2026
**URL:** https://simonwillison.net/2026/Sep/24/datasette/

## Resumo

Alpha 41 do Datasette 1.0 com duas mudanças estruturais:

1. **OpenTelemetry** — Alec Garcia adicionou suporte a telemetry instrumentada no Datasette (docs em internals.html#internals-telemetry). Observabilidade de primeira classe num app Python de data publishing.
2. **Modais como Web Component** — todos os modal dialogs do Datasette foram refatorados num único Web Component, agora documentado para plugins de terceiros reutilizarem (javascript_plugins.html#javascript-plugins-modals).

## Ideias principais

- O pattern "componente de UI core extraído e exposto para plugins" é como plataformas amadurecem: em vez de cada plugin reinventar modal, existe um primitivo suportado.
- OpenTelemetry no Datasette sinaliza que o stack de observabilidade Python já é padrão de facto mesmo em ferramentas pequenas — relevante para qualquer serviço que rodemos no cluster (Olympus).

## Notas e conexões

- Linhas de release anteriores: [[Simon Willison-datasette 1.0a38]].
- Conecta com o tema do patrocínio recorrente do blog (Teleport/Dynatrace): "quando agentes entram no SDLC, observabilidade vira o habilitador" — ver [[Simon Willison-Note on 24th September 2026]].
- [[slipbox/References]]
