---
title: "datasette-llm 0.1a11 — agentes de dados com modelos locais"
source: https://simonwillison.net/2026/Nov/14/datasette-llm/
date: 2026-11-15
tags: [ia, llm, datasette, modelos-locais, automacao]
---

Release note curta, mas com implicação grande: o `datasette-llm` é o plugin intermediário do Datasette que permite configurar LLMs para outros plugins consumirem — o Datasette Agent, por exemplo, depende dele para funcionar. A novidade da versão 0.1a11 é suporte a endpoints compatíveis com a API da OpenAI, o "pseudo-padrão" que virou linguagem comum de toda ferramenta de inferência.

Na prática, isso significa que qualquer backend que fale o protocolo OpenAI entra no time: LM Studio, Ollama e llama.cpp (que acabou de chegar à v1.0.0). Willison demonstra com um único comando `uvx` subir um Datasette com o Agent rodando contra um modelo local (`qwen3.8-27b` via LM Studio em localhost), sem chave de API, sem nuvem — e o agente responde perguntas sobre o banco de dados chamando ferramentas como `sql_query` e `list_databases_and_tables`. O modelo roda na sua máquina; os dados nunca saem dela.

O ponto estrutural é a arquitetura: um plugin intermediário desacopla "qual LLM" de "quem usa o LLM". Os plugins de agente/IA não precisam saber se atrás existe GPT, um Qwen local ou um endpoint no VPS — só precisam do contrato. É o mesmo movimento que LiteLLM fez para a camada de proxy, agora replicado dentro do ecossistema Datasette.

## Por que importa

- O padrão "endpoint compatível com OpenAI" é exatamente o desenho do LiteLLM no VPS do Boss — dá para plugar o Datasette Agent no litellm.ramoneees.com e ter agente SQL sobre qualquer base com o mesmo contrato que os agentes Hermes já usam.
- Modelo local + agente sobre dados = o cenário que volta quando o Qwen local ressuscitar (28GB): agente de consultas 100% offline sobre dados da casa, sem mandar nada pra nuvem.
- Exemplo enxuto de boa engenharia de plugin: contrato intermediário (datasette-llm) separando provedores de consumidores — mesmo princípio port-driven que o Boss aplica nos serviços do precisase.

## Frases notáveis

> "This release adds support for OpenAI-compatible endpoints, so you can configure Datasette to use an LLM hosted anywhere that talks the OpenAI pseudo-standard web protocol."

> "And you'll get a local server running a Datasette Agent instance powered by your local model!"
