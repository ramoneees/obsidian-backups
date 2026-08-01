---
title: "Stateless MCP has recaptured my interest (and inspired mcp-explorer and datasette-mcp)"
source: https://simonwillison.net/2026/Jul/31/stateless-mcp/
date: 2026-08-01
tags: [MCP, IA-agentes, devops, LLM-tools]
autor: Simon Willison
publicacao: Simon Willison's Weblog
---

## Resumo

Simon Willison revive o entusiasmo pelo Model Context Protocol após a publicação da especificação **MCP 2.0 (2026-07-28)**, apelidada informalmente de "Stateless MCP". O MCP, lembra, é o padrão da Anthropic para expor tools a agentes LLM — lançado em novembro de 2024, viveu um pico em 2025 e depois perdeu terreno para "Skills" (outra invenção da Anthropic) quando ficou claro que um agente com terminal + `curl` fazia a mesma coisa de modo mais flexível.

O ponto que muda o jogo agora é arquitetural. O **MCP "legado"** exigia duas chamadas HTTP: uma para inicializar a sessão e obter `Mcp-Session-Id`, outra para chamar a tool — implicando state server-side e roteamento sticky. O **MCP stateless** colapsa tudo numa única request com headers dedicados (`MCP-Protocol-Version`, `Mcp-Method`, `Mcp-Name`). Resultado: clientes e servidores ficam dramaticamente mais simples, escalam melhor em web apps e dispensam sticky sessions.

Willison apresenta dois projetos que saíram diretamente disso. **mcp-explorer** é uma CLI Python instalável via `uvx` que permite listar, inspecionar schemas e chamar tools de qualquer servidor MCP — útil para auditoria sem precisar montar um agente completo. **datasette-mcp** é um plugin Datasette que adiciona endpoint `/-/mcp` com três tools: `list_databases()`, `get_database_schema(name)` e `execute_sql(name, sql)` — read-only por enquanto. Ambos foram viabilizados porque a nova spec reduziu a fricção de implementação a ponto de um fim de semana ser suficiente.

A tese de fundo é pragmática: dar a um agente acesso irrestrito ao shell é arriscado e exige modelo forte. MCP tools são auditáveis, controláveis e simples o bastante para modelos menores rodando em laptop ainda funcionarem razoavelmente — um ganha-ganha de segurança e democratização.

## Por que importa

- **Mudança concreta na stack de agentes**: se Ramon está construindo qualquer coisa com LLMs (provavelmente sim, dado o perfil), MCP stateless reduz atrito e elimina dor de cabeça com state — vale acompanhar de perto.
- **Padrão de "CLI como ferramenta de aprendizado"**: o método do Willison (escrever CLI de exploração antes de escrever código de produção) é replicável e útil para qualquer dev que esteja aprendendo uma nova spec.
- **Filosofia "menor privilégio" aplicada a agentes**: a justificativa do artigo para preferir MCP a shell access alinha com princípios clássicos de devops e segurança — conversa bem com automação e infraestrutura como código.

## Frases notáveis

> "Giving an agent a shell environment with the ability to access the internet is fraught with risk... MCP tools are easier to audit and control, and simple enough that smaller models that run on a laptop can still drive them reasonably well."

> "I find building CLI tools like this to be a really productive way to get familiar with a specification, even if an agent writes most of the actual code."
