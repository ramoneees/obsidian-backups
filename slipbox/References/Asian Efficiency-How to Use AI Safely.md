---
source: Asian Efficiency
title: "How to Use AI Safely: Passwords, Privacy, and Data Rules"
url: https://www.asianefficiency.com/technology/how-to-use-ai-safely/
published: 2026-07-16
ingested: 2026-07-16
category: Technology
tags: [ai, privacy, security, productivity]
---

# How to Use AI Safely: Passwords, Privacy, and Data Rules

**Source:** Asian Efficiency
**Author:** Thanh Pham
**Date:** 2026-07-16 (last updated 2026-07-06)
**URL:** https://www.asianefficiency.com/technology/how-to-use-ai-safely/

## Resumo

Quatro regras práticas para usar IA sem vazar dados sensíveis. Thanh parte do caso óbvio (nunca digitar senhas ou SSNs no ChatGPT/Claude/Gemini) e escala para controles mais finos (opt-out de treinamento, contas separadas, planos Enterprise com proteção contratual).

## Regras Principais

### 1. Nunca digite credenciais em chatbot
Senhas, SSNs, números de cartão, códigos 2FA, prontuários médicos, qualquer coisa sob NDA. A conversa passa pelos servidores da empresa — fica logada e pode vazar. Solução: gerenciador de senhas (1Password Individual $3.99/mês) que nunca expõe credenciais na janela de chat.

> Modelo mental: "se cabe em cofre fechado, não vai em chatbot."

### 2. Desligue o opt-in de treinamento
Em 2026, todas as três plataformas principais (ChatGPT, Claude, Gemini) usam suas conversas para treinar modelos futuros por padrão — incluindo Claude desde setembro de 2025.

| Plataforma | Onde desativar | Observação |
|---|---|---|
| ChatGPT | Settings → Data Controls → "Improve model for everyone" OFF | Temporary Chat = nada salvo |
| Claude | Settings → Privacy → toggle de treinamento OFF | Sem opt-out = 5 anos de retenção |
| Gemini | Google Account → Gemini Apps Activity OFF | Sem Activity = histórico apagado |

### 3. Contas separadas para trabalho vs. pessoal
Mesmo email/login não pode misturar conversas de cliente com chat pessoal. Cinco minutos para configurar; depois nunca mais você se pergunta "qual conta tinha aquela conversa?". Para trabalho sério de cliente, vale pagar Team/Enterprise e separar formalmente.

### 4. Enterprise para trabalho sensível
ChatGPT Team/Enterprise, Claude for Work ($25-30/usuário/mês), Gemini for Workspace — todos têm proteção contratual contra treinamento. O opt-out do plano consumer depende de você lembrar de manter o toggle.

## Tabela de Retenção (planos consumer)

- **ChatGPT Free/Plus:** histórico indefinido (se training ON); 30 dias para abuse monitoring (se training OFF)
- **Claude Free/Pro/Max:** até 5 anos de retenção de-identificada (ON) ou 30 dias (OFF)
- **Gemini Consumer:** salvo e treinável (ON) ou apagado e não-treinável (OFF)

## O que compartilhar / o que não compartilhar

**OK:** tarefas genéricas de trabalho, descrições anonimizadas, pesquisa pública, edição de conteúdo não-confidencial, brainstorming, sua própria escrita sem dados pessoais.

**Não OK:** senhas, SSNs/passaportes, dados bancários, nomes de clientes + detalhes privados (a menos que esteja em plano Enterprise), registros médicos, qualquer coisa sob NDA.

**Teste prático:** "se essa conversa aparecesse num dataset de treinamento futuro, eu ficaria confortável?"

## Por que 1Password pertence ao setup de IA

O fluxo com IA deixa você solto, digitando rápido, colando mais, compartilhando mais. É quando acontecem os erros (colar credenciais em chat em vez de formulário). Gerenciador de senhas elimina a tentação — nada precisa estar no clipboard esperando para vazar.

## Notas e Conexões

- Artigo continua a série de IA + segurança da AE; vê também [[Asian Efficiency-The Real Bottleneck in AI Isn't the AI, It's Your Data]] sobre contexto de dados.
- Conceitos centrais: shadow IT → AI tools sem governança. Cross-link com [[Asian Efficiency-Before Your Next Hire, Run This Experiment First]] (governança de processo) e [[Asian Efficiency-Best AI Tools for Sales and CRM (2026)]] (onde os controles de privacidade aparecem na prática em CRMs).
- Pragmatismo de Thanh: "tabela de retenção" por plataforma seria útil como referência rápida na [[slipbox/templates/reference-note-template]].
- Conexão teológica/ética: o cuidado com dados de terceiros tem paralelo com [[slipbox/Inbox]]/temas de fidelidade e stewardship — não citei, mas vale a reflexão.
