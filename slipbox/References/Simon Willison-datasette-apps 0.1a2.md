---
title: "datasette-apps 0.1a2"
source: Simon Willison
date: 2026-06-15
url: https://simonwillison.net/2026/Jun/15/datasette-apps/
category: Release
tags: [datasette, release, plugins, sandbox, csp]
ingested: 2026-06-19
blogwatcher_id: 752
type: beat (release announcement)
---

# datasette-apps 0.1a2

> Simon Willison — beat (release announcement)

## Resumo

Release 0.1a2 do plugin **datasette-apps** (apps que vivem dentro do Datasette).

## Mudanças

- Origens de rede/CSP customizadas para apps agora são guardadas por uma nova permissão **`apps-set-csp`**, com allow-list opcional de plugin `allowed_csp_origins` para usuários não-privilegiados. A tool de criação de apps do Datasette Agent aplica as mesmas regras. ([#24](https://github.com/datasette/datasette-apps/issues/24))
- Picker de stored query agora suporta **navegação por teclado** e mostra as três stored queries acessíveis mais recentes quando focado.
- Links `#fragment` dentro de apps **não são mais interceptados** pelo modal de confirmação de link externo. ([#23](https://github.com/datasette/datasette-apps/issues/23))
- Modal de confirmação de link e painéis de logging **consertados** no modo full-screen `?full=1`. ([#26](https://github.com/datasette/datasette-apps/issues/26))

## Notas e Conexões

- Conecta com [[Simon Willison-Datasette Apps: Host custom HTML applications inside Datasette]] — post principal anunciando o plugin. Esta release é a primeira iteração pública.
- Conecta com [[Simon Willison-datasette-apps 0.1a3]] — release seguinte, lançada no mesmo dia (3 horas depois).
- Conecta com [[Simon Willison-datasette-acl 0.6a0]] — outro plugin relacionado, expandindo o sistema de permissões.
- Link para o release: https://github.com/datasette/datasette-apps/releases/tag/0.1a2
