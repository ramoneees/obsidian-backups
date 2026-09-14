---
title: "commit-rewriter 0.1"
source: "https://simonwillison.net/2026/Sep/14/commit-rewriter/"
date: 2026-09-14
tags: [ia, devops, git]
---

Simon Willison lançou um web app Python mínimo (`uvx commit-rewriter`) para reescrever mensagens de commit em massa. O gatilho foi real: os commits das releases de segurança do Datasette estavam cheios de "cruft de agente de código" e referências a issue IDs de repositório privado — impróprios para publicação.

A ferramenta é simples: aponta para o repo, lista os commits numa interface web com busca e diff, você edita as mensagens em textarea, e no submit ela cria um branch com timestamp do estado atual (reversível) antes de reescrever todo o histórico do primeiro commit editado até o HEAD.

O detalhe que vale o arquivo: um dos engenheiros mais influentes em LLMs admitting que os commits gerados por agentes precisam de uma etapa de curadoria humana antes de virar histórico público. O fluxo de trabalho com agentes de código não elimina o git hygiene — cria uma nova fase de pós-processamento: agentes escrevem o código, humanos editam o registro público.

## Por que importa

- **Direto no seu fluxo**: você delega todo o coding ao OpenCode/Sisyphus — commits com "cruft de agente" e refs de issues privadas é problema que você já tem ou vai ter. Isso é ferramenta de pipeline, não novidade curiosa.
- **Padrão emergente em AI-assisted programming**: o histórico de commits vira artefato publicado que precisa de curadoria, igual README ou changelog. Agentes geram; humanos assinam o registro.
- **Backup branch antes de reescrever**: padrão de segurança que você aplica em automação (snapshot antes do risco) aplicado ao git — barato e reversível.

## Frases notáveis

> "The initial commits were full of coding agent cruft and references to issue IDs from our private repository, so they weren't fit for publication."

> "When you submit your edits the tool creates a timestamped branch of your current repo state - to allow you to revert if you need to - and then rewrites every commit from the first one you edited to the most recent."
