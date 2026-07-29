---
title: "How to Set Up AI Plugins in Obsidian"
source: Asian Efficiency
author: Thanh Pham
date: 2026-07-29
ingested: 2026-07-29
url: https://www.asianefficiency.com/technology/obsidian-ai-plugins-setup/
category: technology
tags: [obsidian, ai, plugins, copilot, smart-connections, text-generator, pkm, asian-efficiency]
---

# How to Set Up AI Plugins in Obsidian

> "Three plugins turn Obsidian into an AI-powered vault: Copilot for chatting with your notes, Smart Connections for surfacing related ideas automatically, and Text Generator for inline writing help. Setup takes about 15 minutes and costs $3-10/month in API usage, or nothing at all if you run a local model instead."

## TL;DR

Três plugins transformam Obsidian em vault AI-powered. Setup total ~15 minutos. Custo: $3-10/mês em API (ou zero com modelo local via Ollama). Copilot é o de maior valor e ponto de partida — Smart Connections e Text Generator são add-ons opcionais.

## Os três plugins

| Plugin | O que faz | Setup time |
| --- | --- | --- |
| Copilot | Chat sidebar para perguntar sobre seu vault | 10 min |
| Smart Connections | Surfaça ideias relacionadas automaticamente | 5 min |
| Text Generator | AI writing help inline, via shortcut | 5 min |

## O que você vai precisar

- Obsidian instalado (free, qualquer plataforma)
- API key da OpenAI (ChatGPT) ou Anthropic (Claude)… ou modelo local free
- 15-20 minutos para setup inicial
- Vault com algumas notas (AI é mais útil quando tem conteúdo)

## 1. Copilot for Obsidian — Melhor AI plugin geral

**O que faz:** Chat sidebar onde você pergunta sobre suas notas, gera conteúdo e recebe AI assistance. Como ter ChatGPT ou Claude built-in, mas com acesso ao vault inteiro.

**Setup (10 min):**

1. Settings → Community Plugins → Browse
2. Buscar "Copilot"
3. Install e enable
4. Copilot settings → adicionar API key (OpenAI ou Anthropic)
5. Escolher default model (GPT-4o, Claude Sonnet, Claude Opus)

**O que dá pra fazer:**

- **Chat com vault:** "What are my notes about weekly reviews?" — Copilot busca e responde com base nas notas reais.
- **Gerar conteúdo:** "Write a summary of everything I've written about AI agents."
- **Ask questions:** Context-aware answers baseadas nas project notes.
- **Resumir notas:** Selecionar nota longa e pedir resumo.

**Por que é #1:** Mais polida experiência de AI chat no Obsidian. Vault-aware context = respostas referenciam suas notas reais, não conhecimento genérico da internet. Suporta múltiplos models.

**Custo:** Plugin free. API usage: ~$0.01-0.03 per query (GPT-4o). Claude similar. Mensal moderate use: $2-10.

## 2. Smart Connections — Melhor para descobrir links

**O que faz:** Analisa vault e surfaça notas semanticamente relacionadas ao que você está escrevendo. Como ter AI que leu o vault inteiro e diz "essa nota de três meses atrás é relacionada ao que você está fazendo agora".

**Setup (5 min):**

1. Install "Smart Connections" via Community Plugins
2. Enable
3. Aguardar indexação do vault (alguns minutos dependendo do tamanho)
4. Abrir Smart Connections panel no right sidebar

**O que dá pra fazer:**

- **Ver notas relacionadas em real-time:** Conforme escreve ou visualiza nota, sidebar mostra notas semanticamente similares
- **Descobrir conexões esquecidas:** Achar notas de meses atrás relacionadas ao trabalho atual
- **Chat com notas:** Perguntas e respostas grounded no vault
- **Construir knowledge maps:** Entender como ideias se conectam pelo vault

**Por que vale:** Torna o graph view mais inteligente. Em vez de só mostrar links explícitos (que requerem linking manual), Smart Connections mostra relações conceituais sem link explícito. As conexões inesperadas são frequentemente as mais valiosas.

**Custo:** Plugin free. Usa AI embedding models. Custo API mínimo (cents para indexar vault grande, depois pennies/dia ongoing).

## 3. Text Generator — Melhor para writing assistance

**O que faz:** Adiciona AI text generation direto nas notas. Cursor em qualquer lugar, trigger o plugin, ele gera texto baseado no contexto. Autocomplete on steroids.

**Setup (5 min):**

1. Install "Text Generator" via Community Plugins
2. Adicionar OpenAI ou Anthropic API key
3. Configurar model preferido e generation settings
4. Set keyboard shortcut (Cmd+J usado pelo autor)

## Notas e Conexões

- Conexão direta com o vault `~/obsidian-vault` — Ramon já usa Obsidian extensivamente como extended brain
- Ver também: [[Asian Efficiency-Best AI Agents for Personal Productivity (2026)]] — contexto mais amplo de AI tools
- Padrão AE: AI no vault = vault-aware context, não internet knowledge genérico
- Custo local (Ollama) = alternativa zero-custo se quiser manter data ownership total