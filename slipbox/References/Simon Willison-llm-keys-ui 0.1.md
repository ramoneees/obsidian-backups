---
source: "Simon Willison"
title: "llm-keys-ui 0.1"
date: 2026-09-20
author: "Simon Willison"
url: https://simonwillison.net/2026/Sep/20/llm-keys-ui/
category: "Release"
tags: [llm, coding-agents, codex, seguranca, api-keys, ferramenta]
ingested: 2026-09-21
---

# llm-keys-ui 0.1

**Fonte:** Simon Willison (weblog)
**Data:** 20 de setembro de 2026
**URL:** https://simonwillison.net/2026/Sep/20/llm-keys-ui/

## Resumo

Release 0.1 do plugin `llm-keys-ui` — uma web UI para configurar API keys do plugin LLM do Simon. Resolve um problema específico: ele passou a usar o Codex Remote para rodar coding agents em várias máquinas controladas pelo celular, e às vezes precisa configurar uma API key nessas máquinas. Não gosta de colar keys dentro de sessões de agente. Com o plugin, manda o Codex rodar `uvx --with llm-keys-ui llm keys-ui --all`, o agente devolve a URL da interface (incluindo IPs de LAN/Tailscale), e ele salva as keys pelo navegador — sem nunca passá-las pelo chat do agente. Depois o agente usa `llm keys get anthropic` dentro de comandos shell quando precisa.

## Ideias principais

- **Segredos nunca atravessam a sessão do agente:** o padrão é "o agente abre um cofre local; o humano deposita a key fora do canal" — a key não aparece no transcript, no contexto nem no histórico do ChatGPT/Codex.
- Padrão transferível para qualquer ambiente com agentes remotos: servidor efêmero em porta local + acesso via Tailscale + UI que *nunca exibe* valores já salvos (só lista nomes: anthropic, openai, openrouter...).
- `uvx --with ...` como distribuição zero-instal: o agente mesmo instala e sobe a tool sob demanda.

## Notas e conexões

- Alinha 1:1 com a convenção do Boss sobre segredos: "segredos via exec --set, nunca get/echo" e a regra de vault (Hermes: nunca digitar password com fill_input) — aqui o Simon chega à mesma conclusão para API keys de agentes: o segredo entra por canal fora-da-conversa.
- Candidato a padrão para as máquinas que rodam a frota OpenCode: em vez de exportar keys no ambiente, subir um keys-ui local via Tailscale.
- Complementa [[Simon Willison-Stop Kicking Off Every AI Task by Hand]] (resumo-stop-kicking-off-every-ai-task-by-hand) no tema operacionalização de coding agents.
- [[slipbox/References]]
