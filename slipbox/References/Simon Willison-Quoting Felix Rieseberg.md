---
title: "Quoting Felix Rieseberg — Cowork move o sandbox do desktop pra nuvem"
source: Simon Willison
url: https://simonwillison.net/2026/Oct/5/felix-rieseberg/
author: Simon Willison
category: claude
date: 2026-10-06
tags: [ia, agentes, anthropic, arquitetura]
ingested: 2026-10-06
---

Felix Rieseberg, da Anthropic, explicou a mudança de arquitetura do Claude Cowork — e Simon Willison colecionou a citação, que vale como documento de direção de produto para agentes.

A versão "antiga" rodava inferência do modelo na nuvem, mas a execução acontecia numa VM que a Anthropic despachava para o computador do usuário, mapeando dentro dela apenas os dados explicitamente adicionados à sessão — tudo por capacidade, segurança e privacidade. O problema: as pessoas amaram o que faziam, mas não o custo em disco, bateria e performance. E fechar o laptop matava o trabalho.

A versão "nova" move inferência e VM para a nuvem. Cada sessão ganha sandbox próprio, sem compartilhar estado com outras sessões. Quando a VM precisa de algo do dispositivo do usuário — um arquivo, por exemplo — o app desktop é o responsável por executar aquela tool call de acesso a arquivos. O padrão é claro: cérebro na nuvem, máquina local virando interface e provedora de ferramentas.

Os ganhos declarados: usar o agente do celular, trabalho que continua rodando com o laptop fechado, potência total sem queimar bateria. Em troca, a confiança no dispositivo local fica mediada por um app que controla o que o sandbox pode tocar.

## Por que importa

- É o blueprint que valida a direção do setup do Ramon: orquestração centralizada (gateway/agentes) com execução local exposta como ferramenta — arquitetura idêntica em espírito ao Hermes.
- Sandbox por sessão sem estado compartilhado resolve contaminação cruzada entre agentes, mas cobra em custo e latência — o trade-off clássico segurança vs. conveniência, agora decidido em produto.
- Sinal de mercado: agentes estão migrando do desktop pra nuvem. Quem tem automação local (scripts, .command, cron) precisa decidir conscientemente o que permanece local e por quê.

## Frases notáveis

> "Each session gets its own sandbox, not sharing state with other sessions."

> "When the VM needs something on the users' device (like a file), the desktop app is responsible for that file access tool call."
