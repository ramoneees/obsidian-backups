---
title: "datasette 1.0a34"
source: "Simon Willison's Weblog"
date: 2026-06-17
url: https://simonwillison.net/2026/Jun/16/datasette/
author: "Simon Willison"
category: "Release Notes"
tags: [datasette, release, sql, open-source, simon-willison, data-tools, annotated-release-notes]
ingested: 2026-06-17
---

# datasette 1.0a34

## Fonte
Simon Willison's Weblog (Release)

## Data
2026-06-17 (publicado 16 Jun 21:31)

## URL
https://simonwillison.net/2026/Jun/16/datasette/

## Resumo

Release do **Datasette 1.0a34** — "An open source multi-tool for exploring and publishing data".

**Feature principal:** ferramentas pra **inserir, editar e deletar linhas** dentro da interface do Datasette. Essas features estão disponíveis em páginas de tabela, e edit/delete também estão disponíveis como action items na página de linha.

**Contexto de motivação:** a inspiração pra essa feature — que é _long overdue_ — foi o [[Datasette Agent]]. Willison adicionou suporte a **SQL writes** no Datasette Agent dias antes, o que destacou o quão absurdo era: você podia inserir e editar linhas via interface de chat, mas não na UI regular do Datasette.

**Visualização:** GIF demonstrando a feature de edição na interface.

## Recursos

- [Release notes no GitHub](https://github.com/simonw/datasette/releases/tag/1.0a34)
- [Datasette Agent](https://agent.datasette.io/) — produto relacionado
- [Post anterior sobre SQL write support no Datasette Agent](https://simonwillison.net/2026/Jun/15/datasette-agent/)
- [Post de hoje (17 Jun) sobre <click-to-play> component](https://simonwillison.net/2026/Jun/17/click-to-play-component/) — usado pra demonstrar essa feature

## Notas e Conexões

- Willison é o criador do Datasette. Cada release é documentada com cuidado e contexto técnico no blog.
- Conecta com [[Datasette Agent]] (produto paralelo de AI agent que faz queries SQL) e com [[datasette-tailscale 0.1a0]] (lançado mesmo dia, plugin pra rodar Datasette em rede Tailscale).
- Para o contexto de Ramon: Datasette é ferramenta útil pra qualquer pessoa com bancos de dados SQLite que queira **explorar, publicar, ou dar AI agent acesso controlado** a dados. O write support novo abre possibilidade de usar como backend pra ferramentas internas.
- Releaser cadence: 1.0a34 (alpha) — está caminhando pra 1.0 estável. Mudanças são frequentemente breaking (sinal de "alpha" / "preview").
