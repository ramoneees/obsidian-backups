---
title: "Release: datasette-auth-github 1.0"
source: Simon Willison
date: 2026-09-19
url: https://simonwillison.net/2026/Sep/19/datasette-auth-github/
author: Simon Willison
category: Technology
tags: [datasette, github, auth, releases, plugins]
ingested: 2026-09-20
---

# Release: datasette-auth-github 1.0

**Fonte:** Simon Willison
**Data:** 19 de setembro de 2026
**URL:** https://simonwillison.net/2026/Sep/19/datasette-auth-github/

## Resumo

Simon Willison lançou a versão 1.0 do datasette-auth-github, plugin que autentica usuários do Datasette contra o GitHub. A motivação foi um bug prático: no site de demonstração agent.datasette.io, as sessões autenticadas não duravam.

## Ideias principais

- **Causa do bug:** o plugin definia cookies sem o parâmetro `Max-Age`, então expiravam no fim da sessão do navegador — o que no Mobile Safari acontece com frequência, independentemente do uso do app. Corrigido na issue #80.
- **Filosofia de versionamento:** Willison está buscando promover plugins estáveis e testados (aqui, contra Datasette 0.65.x e 1.0ax) para 1.0 — "1.0" como sinal de estabilidade, não de feature-freeze.

## Notas e conexões

- Padrão útil para qualquer app web com login em Safari móvel: cookies de sessão sem `Max-Age` somem de forma imprevisível. Vale conferir nas configurações de auth dos projetos próprios.
- Relacionado ao ecossistema de notas existentes: [[Simon Willison-datasette 1.0a40]], [[Simon Willison-Datasette Apps: Host custom HTML applications inside Datasette]]
- [[slipbox/References]]
