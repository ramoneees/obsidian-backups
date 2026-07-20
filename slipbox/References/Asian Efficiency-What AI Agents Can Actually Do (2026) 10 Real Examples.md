---
source: Asian Efficiency
title: "What AI Agents Can Actually Do (2026): 10 Real Examples"
author: Thanh Pham
date: 2026-07-20
url: https://www.asianefficiency.com/technology/what-ai-agents-can-do/
category: Technology / AI Agents
tags: [ai-agents, productivity, automation, lindy, claude, case-studies]
ingested: 2026-07-20
---

# What AI Agents Can Actually Do (2026): 10 Real Examples

**Source**: Asian Efficiency (Thanh Pham)
**Date**: 2026-07-06 (last updated); discovered 2026-07-20
**URL**: https://www.asianefficiency.com/technology/what-ai-agents-can-do/

## TL;DR

Dez agentes reais que Thanh construiu e implantou para clientes — não hipotéticos. Cobrem email drafting, scheduling, propostas, follow-ups, suporte. O veredito: agentes resolvem 80% do trabalho repetitivo (drafting, scheduling, follow-ups); ainda não substituem julgamento relacional, situações genuinamente novas, ou leitura de ambiente. Recomendação de entrada: começar pelo **Meeting Follow-Up Drafter** — o mais fácil de construir e o de uso mais imediato.

## Os 10 Agentes (resumo)

| # | Agente | Função | Resultado |
|---|--------|--------|-----------|
| 1 | **Digital Chief of Staff** | Pré-redige emails, briefings diários, follow-ups automáticos | 10-20h/semana recuperadas |
| 2 | **Virtual Scheduler (Linda)** | CC no email → checa calendário, propõe horários, agenda | ~1h/dia economizada |
| 3 | **Proposal Generator** | Ouve discovery call, gera proposta customizada do transcript | Propostas saem em minutos vs dias |
| 4 | **Meeting Follow-Up Drafter** | Lê transcript, draft email com pontos-chave e action items | 30min/dia + consistência |
| 5 | **Sales Lead Generator** | (resumo parcial — ver cache file) | Lead intelligence automatizada |
| 6 | (não lido — truncado em 6KB) | — | — |
| 7-10 | (idem) | — | — |

## Padrões que aparecem

- **Lindy + Claude** é a stack padrão. Lindy é o orquestrador no-code; Claude é o cérebro.
- **O truque do delay de 3 minutos no scheduler** (Linda) — replies em 60s parecem suspeitos. O delay humaniza.
- **Configurações de cliente viram constraints** no agent: "Hudson só atende 1-5pm, max 3 calls/dia" → baked into the agent.
- **Proposta como commodity**: CPAs enviando a mesma proposta com nome e data trocados foi o caso clássico. Automação custa $10-15k build + $200-300/mês ongoing.
- **Follow-up em 2 minutos** pós-call fecha mais deals porque a conversa ainda está fresca na cabeça do prospect.

## Por que importa

Não é hype de "AI agents vão mudar tudo" — é inventário do que já está rodando em produção para clientes reais. Cada agente tem métrica de tempo/dinheiro economizado, não só uma demo.

A escolha do **Meeting Follow-Up Drafter como ponto de entrada** é estratégica: baixo risco (drafts only, humano revisa antes de enviar), alto valor (usado em literalmente toda call), simples de construir.

## Notas e Conexões

- [[The AI Stack for Consultants (2026) $34 to $469-Month]] — complementa: stack de ferramentas vs os agentes que rodam em cima
- [[Build Your First AI Agent (2026) A No-Code Beginner's Guide]] — passo-a-passo para construir o primeiro agente
- [[The One Google Doc That Keeps All Your AI Agents in Sync]] — orquestração entre múltiplos agentes
- [[The Payload System: Why Your AI Workflows Are Slow]] — performance de workflows AI
- [[The Librarian Analogy: Why Specialized AI Agents Beat One Big Agent]] — por que specialized agents > monolithic

## Citações-chave

> "Agents handle the 80% of work that's predictable and repetitive — email drafting, scheduling, proposals, follow-ups. They can't yet replace relationship judgment, handle truly novel situations, or read a room."

> "Start with the meeting follow-up drafter — it's the easiest to build and you'll use it after your very next meeting."