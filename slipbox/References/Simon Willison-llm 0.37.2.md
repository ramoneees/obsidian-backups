---
title: "llm 0.37.2"
source: "Simon Willison"
date: 2026-11-11
url: "https://simonwillison.net/2026/Nov/11/llm/"
author: "Simon Willison"
category: "Release"
tags: [release, llm-cli, security, ia]
blogwatcher_id: 1319
ingested: 2026-11-12
---

# llm 0.37.2

**Fonte:** Simon Willison (Simon Willison, Release) | **Data:** 2026-11-11 | **URL:** https://simonwillison.net/2026/Nov/11/llm/

## Resumo

Patch de segurança do LLM (GHSA-v9h7-jj4g-f862 e GHSA-r639-rr7r-x72w), reportado por Daniel de Araujo. O mecanismo extra-openai-models.yaml — agora gerido pelo comando novo do 0.37, `llm openai endpoint add` — podia enviar a sua API key da OpenAI para um provider de terceiros em dois cenários: quando a key nomeada em api_key_name nunca tinha sido armazenada, e quando um modelo configurado com responses: true era rodado com `-o chat_completions 1`.

## Ideias principais

- Superfície de ataque sutil de "compatibilidade OpenAI": o mesmo valor de credencial atravessa providers diferentes por padrão de configuração — reuso implícito de chave é o bug, não o formato do YAML.
- Os dois vetores são ambos casos de fallback silencioso: a key certa não existe (ou não se aplica), e a CLI manda a default sem avisar.
- Achado por usuário externo, não por auditoria interna — report de segurança em projeto open-source pequeno continua sendo o canal mais efetivo.

## Notas e conexões

- Atualização obrigatória para quem usa endpoints customizados. Release anterior: [[Simon Willison-llm 0.37.1]].
- [[slipbox/References]]