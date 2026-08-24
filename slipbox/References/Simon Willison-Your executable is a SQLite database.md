---
title: "Your executable is a SQLite database"
source: Simon Willison
date: 2026-08-24
url: https://simonwillison.net/2026/Aug/24/your-executable-is-a-sqlite-database/
category: Link Blog
tags: [sqlite, linux, elf, binfmt-misc, engenharia]
ingested: 2026-08-24
---

# Your executable is a SQLite database

**Fonte**: Simon Willison — *link blog* (aponta para Farid Zakaria)
**Data**: 2026-08-24 · **URL**: https://simonwillison.net/2026/Aug/24/your-executable-is-a-sqlite-database/

## Resumo

Simon destaca um padrão Linux engenhoso de Farid Zakaria ([post original](https://fzakaria.com/2026/08/23/your-executable-is-a-sqlite-database)): um ficheiro SQLite que é, ao mesmo tempo, um executável ELF válido.

**Como funciona:**
- O campo *application ID* de 4 bytes do formato SQLite (no offset 68 do ficheiro) é setado para `SELF` — *Structured Executable & Linkable Format*.
- Os vários componentes do formato ELF são organizados em tabelas SQLite distintas, seguindo [este schema](https://github.com/fzakria/selfdb/blob/main/schema/self.sql) (repo: `fzakaria/selfdb`).
- Um interpretador `self-exec` ([C code](https://github.com/fzakaria/selfdb/blob/main/loader/self-exec.c)) extrai e executa as peças necessárias.
- Com `binfmt_misc` do Linux, ensina-se o kernel a executar qualquer binário que case com esse padrão (Farid usa NixOS; sem NixOS: registar em `/proc/sys/fs/binfmt_misc/register`).

Simon nota que se pode consultar o executável com ferramentas SQLite normais — o binário vira uma base de dados introspectável.

## Notas e Conexões

- Toque final apropriado: Simon é o autor do `sqlite-utils` — ver [[Simon Willison-sqlite-utils 4.0rc2, mostly written by Claude Fable (for about $149.25)]] e [[Simon Willison-Mapping SQLite result columns to source table columns]].
- Lembrei [[Simon Willison-Claude Fable is relentlessly proactive]] — diferente da maioria dos posts recentes sobre LLMs: puro brinquedo de sistemas.
- Caso de uso prático: um binário que é também BD — metadata versionada, introspecção com SQL, empacotamento único.
