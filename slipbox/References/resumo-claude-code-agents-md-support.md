---
title: "Claude Code agora suporta AGENTS.md (via Thariq Shihipar)"
source: https://simonwillison.net/2026/Sep/18/thariq-shihipar/
date: 2026-09-19
tags: [ia, claude-code, coding-agents, automacao]
---

A Anthropic anunciou (via Thariq Shihipar, equipe do Claude Code) suporte a AGENTS.md a partir da versão 2.1.277: se não houver CLAUDE.md numa pasta, o Claude passa a procurar e usar o AGENTS.md. O AGENTS.md é o padrão vendor-neutro que OpenAI, Cursor e outros já adotam — um único arquivo de instruções por repositório serve a qualquer agente.

O mais interessante é a implementação: o suporte não foi hard-coded, foi construído como um "mod" — o mecanismo novo de customização do harness do Claude Code. E a fonte do mod está pública no GitHub, junto com outros mods, servindo de exemplo de como construir customizações próprias de instruções de projeto.

Na prática, isso reduz duplicação: quem mantém CLAUDE.md e instruções separadas para outras ferramentas pode consolidar num AGENTS.md na raiz e deixar cada harness decidir como consumi-lo. Menos arquivos, menos drift entre agentes.

## Por que importa
- Consolida instruções de agente num único arquivo vendor-neutro: repos como precisase e pack podem migrar de CLAUDE.md para AGENTS.md sem perder nada no Claude Code.
- O "mods" do Claude Code abre caminho para empacotar convenções de projeto (port-driven services, fakes in-memory) como mods reutilizáveis entre worktrees.
- Fonte do mod é pública — referência prática para customizar o harness sem hackear o settings.

## Frases notáveis
> "Starting today in version 2.1.277, if there is no CLAUDE.md in a folder, Claude will check for and use AGENTS.md."

> "AGENTS.md support is built off of Claude Code mods, our upcoming way to customize the Claude Code harness."
