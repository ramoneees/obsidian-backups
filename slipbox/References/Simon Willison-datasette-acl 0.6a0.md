---
title: "datasette-acl 0.6a0"
source: Simon Willison
date: 2026-06-18
url: https://simonwillison.net/2026/Jun/18/datasette-acl/
category: Release
tags: [datasette, release, permissions, acl, plugins]
ingested: 2026-06-19
blogwatcher_id: 750
type: beat (release announcement)
---

# datasette-acl 0.6a0

> Simon Willison — beat (release announcement)

## Resumo

Release 0.6a0 do plugin **datasette-acl** — gerenciamento avançado de permissões para Datasette.

**Esta release expande `datasette-acl` de permissões só-de-tabela para um sistema geral de resource-sharing.**

A maior parte do trabalho foi de **Alex Garcia** — fleshing out do plugin que vai permitir que instâncias multi-usuário do Datasette tenham **controle fino de quem pode acessar quais recursos** dentro do Datasette.

## Notas e Conexões

- Conecta com [[Simon Willison-datasette-apps 0.1a2]] e [[Simon Willison-datasette-apps 0.1a3]] — o sistema de permissões do datasette-apps (CSP, create-app, edit/delete) é construído sobre `datasette-acl`.
- Conecta com [[Simon Willison-Datasette Apps: Host custom HTML applications inside Datasette]] — apps rodam dentro do Datasette, então herdam e dependem de todo o sistema de permissões.
- Tendência do projeto Datasette: **separar permissões em camadas** (tabela, recurso, app, network/CSP). Cada camada com seu plugin.
- Link para o release: https://github.com/datasette/datasette-acl/releases/tag/0.6a0
