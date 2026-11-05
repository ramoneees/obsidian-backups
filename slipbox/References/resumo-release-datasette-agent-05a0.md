---
title: "Release: datasette-agent 0.5a0"
source: https://simonwillison.net/2026/Nov/3/datasette-agent/
date: 2026-11-05
tags: [ia, agentes, datasette, devtools]
---

Simon Willison marcou uma release significativa do Datasette Agent (0.5a0), o agente LLM-powered para o Datasette. A feature central se chama panel: o chat do agente abre e senta ao lado de páginas do Datasette — uma tabela, uma query — em tela dividida. O agente deixa de ser uma janela de conversa isolada e passa a trabalhar com o artefato de dados visível do lado.

Combinado com o datasette-apps, o fluxo fica provocativo: você prompta um app backed-por-banco de dados à existência e depois o modifica pelo chat que fica ao lado do app. No screenshot da release, um "LLM Price Explorer" nasce de um prompt, recebe tool calls (app_create, app_render, app_str_replace) e itera até a versão v2 com estética "hacker" — neon verde em monospace sobre preto — sem nenhuma UI escrita à mão.

É uma beat curta, mas aponta pra onde a interface de agentes de dados está convergindo: pair-programming com dados, onde o agente produz e o resultado aparece no mesmo espaço da conversa. Dá pra testar em agent.datasette.io com login GitHub.

## Por que importa

- O padrão de UI (chat âncora + artefato lado a lado) é o mesmo modelo mental do teu fluxo com agentes no OpenCode: o agente produz, o humano revisa o artefato — só que aplicado a dados.
- Automação sobre dados que já existem: Datasette + agente é literalmente o teu princípio de só automatizar quando os dados já estão num sistema externo (SQLite, n8n, Cockpit).
- App descartável gerado por prompt é uma alternativa barata pra dashboards internos — sem construir UI na mão cada vez que surge uma pergunta nova sobre os dados.

## Frases notáveis

> "it lets the agent chat open and then sit next to pages from Datasette, for example a table or query page."

> "you can prompt a database-backed app into existence and then modify it from the chat that sits next to that app."
