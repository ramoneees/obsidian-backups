---
title: "Datasette Apps: Host custom HTML applications inside Datasette"
source: https://simonwillison.net/2026/Jun/18/datasette-apps/
date: 2026-06-19
tags: [datasette, sandboxing, iframes, csp, ai, generative-ai, devops, simon-willison]
---

## Resumo

Simon Willison lançou o plugin **datasette-apps** — um mecanismo para hospedar aplicações HTML+JavaScript autocontidas dentro de uma instância Datasette, executadas dentro de um `<iframe sandbox="allow-scripts allow-forms">` reforçado por Content Security Policy (CSP). Apps podem rodar queries SQL de leitura contra o banco e, opcionalmente, queries de escrita via "stored queries" pré-configuradas.

A ideia nasceu de uma necessidade concreta: o Datasette Agent (interface de IA agêntica sobre Datasette) precisava de um equivalente ao Claude Artifacts. Mas Willison percebeu que o padrão "backend relacional + frontend HTML isolado em sandbox" é interessante para muito mais do que IA — é um padrão arquitetural genérico. O CSP injetado bloqueia requisições para hosts externos, impedindo exfiltração de dados mesmo por apps maliciosas ou bugadas.

O ponto filosófico do post: combinar um backend SQL persistente e versionável com frontends descartáveis e vibe-coded muda o que significa "construir uma aplicação interna". Não é mais "frontend + backend + deploy + auth" — é "escreva o HTML, escreva a query, deixe o iframe fazer o resto". Willison argumenta que esse é o caminho para tornar ferramentas internas de uma pessoa só realmente úteis.

## Por que importa

- Para o Ramon que trabalha com IA/ML e devops: esse padrão (sandbox + CSP + backend SQL + frontend descartável) é uma das arquiteturas mais pragmáticas para ferramentas internas agênticas. Vale estudar como referência para qualquer projeto de "agentes com estado".
- O exemplo mental — "como Claude Artifacts seria se tivesse acesso a um banco relacional persistente" — é exatamente o tipo de insight que conecta IA generativa a tooling sério. Vale arquivar como ponto de partida para experimentos próprios.
- Willison cita Kate Moussouris e o caso Fable 5 no mesmo contexto temporal — útil como contraste entre "IA agêntica útil com sandbox" e "IA agêntica perigosa sem governança".

## Frases notáveis

> "Imagine how much more useful Claude Artifacts could be if they had access to a persistent relational database. That's what I'm building with Datasette Apps!"

> "Adding a Datasette-style backend to a self-contained HTML frontend is an astonishingly powerful combination."
