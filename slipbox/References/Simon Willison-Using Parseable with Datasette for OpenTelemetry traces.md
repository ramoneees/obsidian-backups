---
title: "Using Parseable with Datasette for OpenTelemetry traces"
source: Simon Willison
date: 2026-10-06
url: https://simonwillison.net/2026/Oct/6/datasette-parseable-opentelemetry/
author: Simon Willison
category: TIL
tags: [datasette, observabilidade, opentelemetry, parseable, ferramentas]
ingested: 2026-10-07
---

# Using Parseable with Datasette for OpenTelemetry traces

**Fonte**: Simon Willison (TIL)
**Data**: 2026-10-06 . **URL**: https://simonwillison.net/2026/Oct/6/datasette-parseable-opentelemetry/

> Parseable: plataforma de observabilidade nova, compatível com OpenTelemetry, com implementação Rust open source (AGPL) num único binário de ~180MB.

## Resumo

TIL nascido de um Show HN: desde que o Datasette 1.0a41 ganhou suporte a OpenTelemetry (graças a Alex Garcia), o Simon usou o Codex para descobrir como rodar o Parseable e alimentá-lo com traces do Datasette. O TIL documenta os padrões que funcionaram, com screenshot de um trace do Datasette exibido na web app local do Parseable.

## Ideias principais

- **Observabilidade self-hosted em um binário**: Parseable aposta em simplicidade operacional (Rust, single binary) contra o complexo stack padrão — opção real para quem não quer montar Grafana+Loki+Tempo.
- **IA como integrador de ferramentas**: o trabalho pesado de descobrir a configuração foi delegado ao Codex; o humano escreveu o TIL do resultado. "Human-written" explícito é o selo de qualidade.
- **Traces como cidadão de primeira classe em tools locais**: o Datasette agora emite OpenTelemetry nativo — instrumentação padrão virou baseline, não diferencial.

## Notas e conexoes

- Datasette em manutenção ativa na semana: [[Simon Willison-datasette-atom 0.11a0]] (o release que permitiu o upgrade do datasette.io para 1.0a41).
- [[slipbox/References]]
