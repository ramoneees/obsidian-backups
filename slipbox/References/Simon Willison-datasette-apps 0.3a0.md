---
title: "datasette-apps 0.3a0"
source: "Simon Willison"
date: 2026-11-04
url: "https://simonwillison.net/2026/Nov/4/datasette-apps/"
author: "Simon Willison"
category: "Release"
tags: [release, datasette, apps, agentes, ia]
blogwatcher_id: 1234
ingested: 2026-11-05
---

# datasette-apps 0.3a0

**Fonte:** Simon Willison
**Data:** 4 de novembro de 2026
**URL original:** https://simonwillison.net/2026/Nov/4/datasette-apps/

## Resumo

Nova versão alpha do Datasette Apps: suporte a hospedar e editar aplicações HTML customizadas dentro do Datasette. Os apps podem ser criados à mão, mas o caminho natural é gerá-los com LLMs via Datasette Agent — e é exatamente essa integração que o release melhora.

## Ideias principais

- Apps viram cidadãos de primeira classe no chat do agente: digitar # autocompleta dos apps que o usuário tem permissão de ver — permissão de visão controla o que o agente pode referenciar.
- Novas tools app_add_stored_queries() e app_remove_stored_queries() deixam o agente gerenciar quais stored queries um app pode chamar; conceder write query exige aprovação do usuário antes.
- app_create() agora valida que cada stored query pedida existe e é visível para o usuário, e pede aprovação de write queries antes de criar o app — não deixa o agente inventar queries.
- Botões "View app" das tools e links das referências # abrem o app em tela cheia no painel do Datasette Agent.
- O padrão de segurança é a gramática de agente em três camadas: visão (autocomplete só do que se pode ver), validação de existência (query tem que existir) e human-in-the-loop para escrita — a mesma lógica de review + aprovação que se usa com agentes de código.

## Notas e conexões

- [[Simon Willison-datasette-llm 0.1a10]] — release irmã do mesmo dia; o fix de restrição de modelos protege o mesmo demo (agent.datasette.io).
- [[resumo-release-datasette-agent-05a0]] — o Datasette Agent é o cliente principal dessa integração de apps.
- [[slipbox/References]]
