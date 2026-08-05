---
source: Asian Efficiency
author: Thanh Pham
title: "How to Build an AI Executive Assistant for Email (Telegram Setup)"
url: https://www.asianefficiency.com/technology/ai-executive-assistant-for-email/
published: 2026-08-05
ingested: 2026-08-05
category: Technology / AI productivity
tags: [ai, ai-agents, telegram, email, productivity, executive-assistant, asian-efficiency]
---

# How to Build an AI Executive Assistant for Email (Telegram Setup)

**Source**: Asian Efficiency (Thanh Pham)
**Published**: 2026-08-05

## TL;DR

Construir um agente de IA que funciona como EA (executive assistant) via Telegram, integrado a CRM e Gmail. A premissa: tarefas de 15 minutos (como emails de apresentação) viram 15 segundos quando o agente já tem contexto sobre os teus contactos, sabe fazer pesquisa fresca, e deposita um rascunho pronto no Gmail.

## A Tese Central

O ponto não é a velocidade de envio — é a velocidade de **drafting**. Quando o rascunho já aparece, basta 1-2 minutos para rever. Tarefa de 2 minutos efetivamente acontece; tarefa de 15 minutos fica na lista para sempre.

## Como Funciona (caso real Thanh)

Demonstração na workshop de novembro passado: Thanh pediu ao agente (via Telegram) para "Draft an email to Evan Baehr to introduce Lauren Goldstein to be a guest at his members club." Em 10 segundos, o email estava nos drafts do Gmail, com:
- Contexto sobre Evan (do CRM pessoal)
- Background da Lauren (do CRM + Google search em background)
- Tom personalizado (não template)

## "AI as Tool vs. AI as Teammate"

Dois modelos distintos:
1. **Tool**: abres, dizes o que queres, ajuda a fazer a coisa. (Como a maioria usa ChatGPT hoje.)
2. **Teammate**: já sabe o teu contexto — contactos, relações, preferências, calendário. Podes dar um pensamento meio-formado e ele descobre o resto.

A magic está no segundo modelo. Um bom teammate não precisa de briefing sobre quem é o Evan cada vez que o mencionas.

## Os 4 Requisitos

1. **Lista de contactos centralizada** que o agente possa ler (Google Sheet bem mantido já basta).
2. **Interface que já usas** (Telegram no caso dele — não abrir app separado).
3. **System prompt bom** (o que torna um intro email bom? tom? formalidade?).
4. **Permissão para pesquisar** (Google fresh context, não só CRM estático).

## Compound Effect

Intro emails compoundam. Um bem-feito pode levar a parceria, contratação, negócio, amizade. Se o agente corta fricção de 15min para 2min, não envias os mesmos mais rápido — envias **mais**. Os que terias deixado passar.

## Conexões

- Relação directa com [[Asian Efficiency-How to Start Building Your Own AI Agents]] (mesmo autor, publicado no mesmo dia) — esta peça é o "caso concreto" (intro email agent) daquela tese mais ampla.
- [[Asian Efficiency-The 30-Minute Meeting Prep Notification]] — outro exemplo do modelo "teammate" com calendar trigger.
- [[Asian Efficiency-Automation Doesn't Just Save Time — It Removes the Ceiling]] (cycle 2026-07-01, stub) — mesma linha de pensamento sobre AI agents.
- Reflexão directa para o workflow do Ramon: o que está descrito aqui é exactamente o que o agente Nina faz para a Renatha (WA → draft → review). A diferença é o canal (Telegram vs WhatsApp) e a trigger (intro email vs qualquer pedido).