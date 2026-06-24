---
title: "The Project Document That Updates Itself"
source: Asian Efficiency
date: 2026-06-23
url: https://www.asianefficiency.com/technology/master-memo/
category: technology
tags: [ai-agents, project-management, knowledge-management, automation]
ingested: 2026-06-24
type: article
---

# The Project Document That Updates Itself

Thanh (Asian Efficiency) introduces the **Master Memo** — a living project document maintained automatically by an AI agent. The case study: Evan, who runs a coworking space and was drowning in fragmented project context spread across Slack, Granola transcripts, and unanswered emails.

## The Problem

Most project documents become fossils. Created with good intentions, then neglected because updating them is overhead. The real source of truth becomes "ask someone who was in the room." This isn't just inefficient — it puts institutional memory in people instead of systems. When someone is out sick or leaves, context walks out with them.

## The Master Memo System

A Master Memo is a living document maintained by an AI agent that:
- Reads incoming emails (filtered by project name, participants, keyword)
- Reads meeting transcripts (Granola, Otter integrations)
- Reads voice notes / async updates
- Surfaces key developments, team commitments, stuck items, and broken promises
- Updates the document on a schedule (daily or weekly)

### Implementation steps

1. **Define the memo structure** — template with: current status, key decisions made, outstanding commitments (with owner), things stuck, open questions.
2. **Connect the agent to inputs** — Gmail filter + transcript tool + Slack channel + voice notes.
3. **Set the update cadence** — daily for fast-moving projects, weekly for slower ones.

## What This Changes

- **Time reclaimed:** 30-60 min/week per team that was being burned on manual status updates.
- **Trust:** people know the document reflects reality, so they don't ping the project lead for status.
- **Institutional memory:** captured in a system, not in people's heads.

The leverage doesn't come from having the files. It comes from agents using them.

## Notas e Conexões

- [[Asian Efficiency]] — source feed
- [[AI agents]] — broader theme; this is a concrete "one agent, one job" pattern
- [[Knowledge management]] — knowledge lives in documents, not in heads
- [[Granola]] — transcription tool referenced for meeting inputs
- Connects to [[extended brain]] pattern — Hermes memory + Obsidian vault as Ramon's analog
- Related: [[Obsidian vault]] as a living document system; the Master Memo is the *project-specific* version of that pattern
- The Vault delivers notes via Git; the Master Memo delivers project status via AI agent. Both push the burden of currency onto automation, not the human.