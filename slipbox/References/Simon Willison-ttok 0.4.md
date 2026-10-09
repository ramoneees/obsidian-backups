---
title: "ttok 0.4"
source: "Simon Willison"
date: 2026-10-08
url: "https://simonwillison.net/2026/Oct/8/ttok/"
category: "Release"
tags: [reference, llm, tokenizer, tiktoken, release, simon-willison]
ingested: 2026-10-09
---

# ttok 0.4

**Fonte:** Simon Willison (release)
**Data:** 8 de outubro de 2026
**URL original:** https://simonwillison.net/2026/Oct/8/ttok/

## Resumo

Atualização do ttok, a CLI do Simon para contar tokens usando a biblioteca tiktoken da OpenAI — depois de um par de anos sem manutenção. Mudanças: fix de um warning do Click, CI atualizada e um novo comando `--list-models` para listar os modelos/tokenizers disponíveis.

## Notas principais

- Funciona com `uvx` — contagem de tokens de qualquer coisa sem instalar nada: `cat file.txt | uvx ttok`.
- Manutenção mínima viável: warning + CI + um comando novo já justificam release.
- Um dia depois veio o [[Simon Willison-ttok 1.0]] (troca do tokenizer default).

## Notas e conexões

- Útil no kit de estimativa de contexto/custo de LLM (mesmo domínio de [[Simon Willison-llm-openrouter 0.7]]).
- [[slipbox/References]]
