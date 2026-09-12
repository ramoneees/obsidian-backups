---
title: "Quoting Boris Cherny"
source: "Simon Willison"
date: 2026-09-11
url: "https://simonwillison.net/2026/Sep/11/boris-cherny/"
tags: [reference, simon-willison, citacao, claude, anthropic, coding-agents, qualidade]
ingested: 2026-09-12
---

# Quoting Boris Cherny

**Fonte:** Simon Willison (quote post)
**Data:** 11 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/11/boris-cherny/
**Origem da citação:** https://twitter.com/bcherny/status/2098217573276131577

## Resumo

Citação de Boris Cherny (Anthropic) sobre o padrão de qualidade para código escrito por IA:

> "Production code written by Claude should have a higher bar than if it was written by a human. At Anthropic, we have many guardrails in place to make sure this is happening: lots of lint rules, lots of tests, Claude-driven end to end tests, Claude-powered fuzzers running daily, automated code reviews and security reviews, automated code refactoring, and so on. Without these, you can end up with a mess that is hard to maintain down the line."

## Ideias principais

- Código de produção gerado por IA pede **barra mais alta** que código humano — não mais baixa.
- Os guardrails da Anthropic: lint rules, muitos testes, **e2e tests dirigidos pelo próprio Claude**, fuzzers alimentados por IA rodando diariamente, code review e security review automatizados, refactoring automatizado.
- Sem isso: bagunça difícil de manter a médio prazo.

## Notas e conexões

- É a mesma direção do que o Simon relata em [[Simon Willison-Datasette 1.0a39 and 0.65.4 security releases]] — usar IA tanto para escrever quanto para auditar, com revisão humana em cima.
- "Qualidade em 1º lugar" aplicado a agentes de código: CI + revisão obrigatória, sem atalho.
- [[slipbox/References]]
