---
source: "Simon Willison"
title: "MCP was always a bad idea?"
date: 2026-09-20
url: https://simonwillison.net/2026/Sep/20/hn-49779718/
author: "Simon Willison"
category: "Blog"
tags: [mcp, ia-agentes, devops, arquitetura]
ingested: 2026-09-22
---

Willison responde no Hacker News a um artigo que declara o MCP (Model Context Protocol) obsoleto — a tese sendo que agentes de terminal com acesso total à internet (Claude Code, Codex e afins) não precisam de uma camada de protocolo para chamar APIs. Ele discorda: a premissa só vale para o canto mais "YOLO" do ecossistema. Para qualquer sistema que precise de limites, o MCP resolve exatamente os problemas difíceis.

O argumento central: agentes autônomos sem freios são fáceis de conectar, mas perigosos de operar. O MCP entrega quatro coisas que o acesso direto a APIs não entrega — controle granular de quais serviços o agente pode acessar, autenticação que não expõe chaves de API ao agente, uma UI sensata para o usuário conectar serviços, e logging de auditoria do que o agente fez. Sem isso, você escolhe entre correr sem cinto ou construir toda essa infraestrutura na mão.

A provocação útil para quem opera agentes em produção: "o agente não precisa de MCP" e "a operação do agente precisa de MCP" são frases diferentes. O valor do protocolo não está no ability de chamar ferramentas, e sim no perímetro de controle, credenciais e auditoria ao redor delas.

## Por que importa

- Você roda agentes em produção (Hermes, n8n, OpenCode) — a discussão "MCP morto vs. necessário" é sobre o trade-off exato que você opera: autonomia total do agente vs. controle de credenciais e auditabilidade.
- O ponto sobre "o agente nunca ver a API key" conecta direto com sua regra de segredos (vault, `exec --set`, nunca ecoar) — o MCP como padrão para não vazar credenciais para o contexto do modelo.
- Willison mostra como responder uma tese provocativa sem strawman: concede o ponto parcial (agentes full-access não precisam) e ataca a generalização. Técnica de escrita técnica que vale observar.

## Frases notáveis

> "If you want to operate something that's less YOLO than that, you'll find yourself wanting: 1. Control over exactly which external services it can access. 2. A way to handle authentication that doesn't allow the agent to directly access API keys. 3. A sensible UI to allow users to connect and authenticate further services. 4. Strong audit logging for what's going on. MCP makes all of that so much easier to provide."

> "Thinking MCP is obsolete because full coding agents don't need it misses out on all of the other things we might want to build."
