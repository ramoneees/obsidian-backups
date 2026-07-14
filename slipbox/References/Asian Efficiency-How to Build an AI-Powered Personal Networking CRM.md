---
source: Asian Efficiency
title: "How to Build an AI-Powered Personal Networking CRM"
date: 2026-07-14
url: https://www.asianefficiency.com/technology/ai-crm-networking/
category: Technology
tags: [crm, networking, airtable, claude, clay, relationships, contacts, slack, automation]
ingested: 2026-07-14
---

# How to Build an AI-Powered Personal Networking CRM

**Source:** Asian Efficiency (Thanh Pham)
**Date:** 2026-07-14
**URL:** https://www.asianefficiency.com/technology/ai-crm-networking/

## TL;DR

A personal networking CRM doesn't need to be Salesforce. It needs to answer **one question**: _who should I be staying in touch with, and when did I last do it?_ Airtable + Claude is the recommended setup (~$40/mo), Google Sheets + ChatGPT covers the basics free, and Clay is worth the higher price only when networking is sales-development. Most people abandon personal CRMs within six weeks because they over-engineer them.

## The 3 setups compared

| Setup | Best for | Cost |
|---|---|---|
| Airtable + Claude | Anyone who wants an AI layer that comes to you (via Slack) | ~$40/mo |
| Clay | Sales-focused networkers needing contact enrichment | $185–$495/mo |
| Google Sheets + ChatGPT | Anyone starting from zero, wants zero cost | Free |

## What a personal networking CRM actually needs

Four fields, nothing more:
1. Contact info (name, email, how you met)
2. Last contact date
3. Notes from the last conversation
4. Next action (follow up? Intro to make? No action needed?)

People who build CRMs with 40 fields fill in three and abandon the rest in six weeks.

## Option 1: Airtable + Claude (Thanh's setup)

**Airtable base structure** — two tables in one base:

- **Contacts table** — Name, Email, Phone, LinkedIn URL, Company/Role, How We Met (dropdown), Last Contact Date, Notes (free text), Next Action, Priority (1–3), Tags.
- **Interactions table** — Date, Contact (linked field), Notes from that conversation, Medium (coffee/email/call/event). Logging each conversation separately is where the gold is; Claude can query across them.

Airtable ships a [free personal CRM template](https://airtable.com/templates/personal-crm).

**Connecting Claude** — Claude Bot runs on a Mac Mini, connects to Airtable via the Airtable API, and is interacted with through Slack. Sample prompts that work:

- "Who haven't I talked to in 60 days?"
- "Show me 5 people I should follow up with this week"
- "When did I last talk to {name}?"
- "Add a note: had coffee with {name} on March 20, talked about their new fund"
- "Who do I know in the VC space in Austin?"

When asked to "add a note," Claude creates a new row in Interactions and updates Last Contact Date automatically. Setup is not five minutes but doable in a few hours with tutorials; Make.com or n8n provide no-code bridges.

### The "Dream 1,000" concept

Maintain ~1,000 high-value contacts (investors, founders, media, clients, close friends). Every morning, Claude surfaces 5 people to reach out to based on: not talked to in 30+ days, Priority 1 or 2, and any relevant recent context (e.g. news).

**Cost:** Airtable Team $20/seat/mo (annual) + Claude Pro $20/mo = ~$40/mo, plus minor API cost.

## Option 2: Clay (sales-focused)

Clay is sales intelligence, not a personal CRM. It auto-enriches contacts — give it a name + company, it finds email, LinkedIn, job changes, funding news, recent mentions. Useful for founders doing outbound fundraising or SDRs managing large prospect lists; not worth it for staying in touch with a professional network.

**Pricing (July 2026, restructured March 2026):** Free (100 credits/mo, very limited), Launch $185/mo, Growth $495/mo. ROI only when networking directly drives revenue.

## Notas e Conexões

- Self-evolving AI agent ("Claude Bot on Mac Mini") reforça o padrão AE de [[Asian Efficiency-Im a Glorified Typing Monkey and That's How I Ship Code Around the Clock]] — Claude como agente persistente orquestrando tools via Slack.
- Pipeline Airtable + Claude → encaixa na pilha de [[Asian Efficiency-Best AI Automation Platforms (2026) Zapier, Make]] (Make/n8n como bridge no-code).
- Quick-capture Slack → Airtable pattern expande o [[Asian Efficiency-6 Zapier AI Email Automations Worth Building]] para além do email.
- "Four fields, no more" é antípoda do Salesforce — espelha a filosofia GTD de [[Allen-Serra-A arte de fazer acontecer - O método GTD - Getting Things Done]] sobre não over-engineer o sistema.
- Concept de "Dream 1,000" → cross-link com [[Asian Efficiency-The 2-Hour Advantage (What a Paralyzed Blogger Taught Me About Ruthless Focus)]] sobre ruthless focus na rede de contatos.
- Slack como interface para AI agents → [[Asian Efficiency-How my email inbox agent saved 18 hours in one week]] já demonstrou esse mesmo padrão (email como domínio).