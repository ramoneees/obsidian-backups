---
title: "Midjourney Scanner 🏥, AWS vs Nvidia ⚡, agent loop architecture 👨‍💻"
source: TLDR AI
date: 2026-06-19
url: https://tldr.tech/tech/2026-06-19
category: Newsletter
tags: [ai, midjourney, aws, nvidia, agents, pricing, mars]
ingested: 2026-06-19
blogwatcher_id: 769
edition: TLDR 2026-06-19
---

# Midjourney Scanner 🏥, AWS vs Nvidia ⚡, agent loop architecture 👨‍💻

> TLDR — edição 2026-06-19

## Resumo

Edição diária do TLDR cobrindo: AWS vendendo chips AI para fora, Midjourney pivotando para health hardware, NASA escolhendo Relativity Space para missão a Marte, e o artigo longo do dia sobre **arquitetura de agent loops**.

## Highlights da edição

### AWS vs Nvidia

**Amazon espera desafiar Nvidia mais diretamente vendendo seus chips AI** (2 min read). AWS está em conversas para vender seus chips **Trainium** para outras empresas usarem em data centers. Resistiu até agora porque a capacidade dos chips atuais já está vendida. Vender para outras empresas pode significar **clientes atuais esperando na fila**, a menos que AWS tenha descoberto como fabricar mais chips (improvável).

→ [TechCrunch](https://techcrunch.com/2026/06/18/amazon-hopes-to-challenge-nvidia-more-directly-by-selling-its-ai-chips/)

### Midjourney Scanner

**AI startup Midjourney pivota para health com máquina de ultrassom** (2 min read). Anunciou projeto de hardware em saúde pessoal/medicina: scanner de ultrassom full-body, o **Midjourney Scanner**, requer que usuários estejam parcialmente submersos em água. Plano de construir frota de 50.000 scanners, primeiro debutando num local "Midjourney Spa" em San Francisco. **Os scanners não usam AI.** Midjourney está trabalhando em **4 hardware + 4 software initiatives**, planejando shipar pelo menos 2 hardware efforts no curto prazo.

→ [Bloomberg](https://www.bloomberg.com/news/articles/2026-06-18/ai-startup-midjourney-pivots-to-health-with-ultrasound-machine)

### NASA → Marte

**NASA escolhe empresa de foguetes de Eric Schmidt para missão a Marte** (3 min read). NASA contratou **Relativity Space** para construir spacecraft, lançar e voar até Marte. Missão **Aeolus** carregará 4 instrumentos para medir e imagear Marte da órbita. Será a primeira visão diária global de poeira, ventos e temperaturas na atmosfera marciana. Dados vão tornar mais seguro para landers e astronautas visitarem a superfície. **Lançamento em 2028.**

→ [TechCrunch](https://techcrunch.com/2026/06/17/nasa-picks-eric-schmidts-rocket-company-for-mars-mission-setting-up-a-race-with-spacex/)

### Token pricing testing AI economics

**Como o modelo de cobrança por medidor está testando a economia de AI** (11 min read). Número crescente de empresas tech introduziu opções de **usage-based pricing** para serviços AI em vez de cobrar flat subscription fee. Mudança para esse modelo pode levar a uso mais seletivo da tecnologia. Forçou empresas a confrontarem seus gastos com AI e avaliarem o **retorno sobre o investimento**.

→ [Bloomberg](https://www.bloomberg.com/news/articles/2026-06-18/ai-costs-what-shift-from-flat-rate-to-token-pricing-model-means-for-industry)

### Agent loop architecture (deep dive do dia)

**The Agent Loop Architecture** (18 min read). Durability é uma propriedade da **camada de execução inteira por baixo de um loop**. Durable orchestration é fundamental para construir uma arquitetura de agent loop. O artigo detalha onde loops tipicamente quebram, o que significa ter durability real, e o trade-off entre simplicidade e resiliência.

## Quick takes

- **Clear (linguagem de programação)** — spec e implementation no mesmo arquivo. Sem translation step ou drift entre docs e behavior. Compila para qualquer target sem mudança na spec. Construída para agentes lerem e executarem enquanto legível por humanos no time.
- Mercury Command (sponsor): AI integrado à conta Mercury que entende linguagem natural e executa pagamentos, invoices, categorização, gestão de time. Você revisa e aprova cada ação.
- Browserbase (sponsor): roda agents em browsers reais. Self-healing quando páginas mudam. 35M+ sessions/mês, 10K+ times incluindo Ramp, Lovable, DeepMind.

## Notas e Conexões

- Conecta com [[Asian Efficiency-You Don't Need to Build AI Agents. You Need to Operate Them.]] — o artigo sobre "agent loop architecture" é justamente sobre **onde loops tipicamente quebram** (problema de operação, não de construção).
- Conecta com [[Asian Efficiency-The Signal I Missed When My AI Workshops Sold Out Twice]] — **token-based pricing** vs flat subscription é o exemplo concreto do "pacing of change": o modelo de cobrança mudou, então o mental model de "como avaliar custo/benefício de AI" precisa ser atualizado.
- Conecta com [[Stratechery-2026.25 The Stuff of Myth(os)]] — chip policy (AWS vs Nvidia) é o lado infra do mesmo debate que Stratechery cobre do lado model-side (Fable/Anthropic).
- **Midjourney Scanner**: pivot contraintuitivo para hardware médico sem AI na máquina. Hipótese: hardware como **distribution channel** para o AI da Midjourney (cloud-side) — o scanner coleta dados, o AI processa. Mesma lógica de Datasette Apps: front-end simples, back-end inteligente.
- **Clear language**: movimento emergente de linguagens "AI-native". Conecta com tentativas de criar linguagens que agentes leem melhor que humanos.
