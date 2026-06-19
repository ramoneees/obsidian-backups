---
title: "Datasette Apps: Host custom HTML applications inside Datasette"
source: Simon Willison
date: 2026-06-18
url: https://simonwillison.net/2026/Jun/18/datasette-apps/
category: Article
tags: [datasette, apps, sandbox, iframe, claude-artifacts, csp]
ingested: 2026-06-19
blogwatcher_id: 749
---

# Datasette Apps: Host custom HTML applications inside Datasette

> Simon Willison — post principal do lançamento

## TL;DR

**Datasette Apps são aplicações HTML+JS auto-contidas que rodam num `<iframe>` sandboxed, hospedadas na sua instância Datasette.** Podem usar JavaScript para rodar SQL queries read-only contra dados no Datasette, e queries de write também se você configurar com stored queries.

## A combinação mágica

```html
<iframe sandbox="allow-scripts" srcdoc="...">
<meta http-equiv="Content-Security-Policy"
      content="default-src 'none'; script-src 'unsafe-inline';
               style-src 'unsafe-inline'; img-src data: blob:;">
```

- `sandbox=` permite rodar código não-confiável **sem** acesso ao DOM pai, cookies, ou localStorage
- `<meta http-equiv="Content-Security-Policy">` previne requests para hosts externos
- **Combinados**: roda HTML+JS não-confiável num domínio altamente sensível sem risco de exfiltração

## A história por trás

Datasette sempre ofereceu backend flexível para criar apps HTML custom via JSON API. Um dos primeiros projetos Datasette de Simon foi uma **search engine interna para documentação** na Eventbrite — funcionava importando documentos de sistemas diferentes para SQLite num cron e servindo via Datasette com uma interface HTML+JS custom que **consultava a API do Datasette diretamente**. JavaScript client-side construindo queries SQL, originalmente como piada de engenharia, virou **maneira muito produtiva de iterar na app**.

Combinado com a experiência de Simon construindo o [HTML tools collection](https://simonwillison.net/tags/html-tools/) e os experimentos com **Claude Artifacts**, o postula:

> "Adicionar um backend estilo Datasette a um frontend HTML auto-contido é uma combinação assombrosamente poderosa. Imagine quanto mais útil Claude Artifacts poderia ser se tivesse acesso a um banco de dados relacional persistente. É isso que estou construindo com Datasette Apps."

## Patterns notáveis

- `<iframe sandbox="allow-scripts" srcdoc="...">` + CSP via `<meta>` tag — a combinação que torna tudo viável
- Apps podem usar `fetch()` e amigos para carregar conteúdo, **mas** CSP bloqueia domínios externos — definido pelo owner da instância Datasette
- Stored queries permitem queries de write controladas — não é "todo mundo pode escrever qualquer coisa"
- Sistema de permissões em camadas (veja [[Simon Willison-datasette-acl 0.6a0]] e [[Simon Willison-datasette-apps 0.1a2]] para o modelo de permissões)

## Por que construir isso

Começou como tentativa de construir um mecanismo tipo **Claude Artifacts para o Datasette Agent**, mas o pattern sandboxed é interessante para muito mais que adicionar apps custom à interface — promoveu para conceito top-level dentro do ecossistema Datasette.

> "Também é uma maneira divertida de transformar meu experimento multi-ano de vibe-coded HTML tools numa feature central do meu projeto principal!"

## Demonstração

Pode testar Datasette Apps assinando com GitHub na instância demo **agent.datasette.io**.

## Notas e Conexões

- Conecta com [[Asian Efficiency-You Don't Need to Build AI Agents. You Need to Operate Them.]] — Datasette Agent é justamente um exemplo do operator role: o agente opera os apps, o usuário opera o agente.
- Conecta com [[Stratechery-2026.25 The Stuff of Myth(os)]] — Anthropic foi destaque da semana; o pattern de Datasette Apps é um contraponto open-source/self-hosted ao Claude Artifacts.
- Conexão profunda: o problema clássico de "AI pode gerar HTML+JS mas onde roda?" — Datasette Apps resolve com sandbox+backend persistente. Mesmo problema que Claude Artifacts resolve, mas com persistência relacional.
- Categoria técnica: o padrão `<iframe sandbox> + CSP meta tag` é o gold standard para rodar código não-confiável num domínio autenticado.
