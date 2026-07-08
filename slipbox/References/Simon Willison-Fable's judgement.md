---
title: "Fable's judgement"
source: "Simon Willison's Weblog"
date: 2026-07-03
url: "https://simonwillison.net/2026/Jul/3/judgement/"
category: ai
tags: [ai, claude-code, agents, fable, model-selection, cost]
ingested: 2026-07-08
---

# Fable's judgement

**Simon Willison** — notes from a Claude Code fireside chat. The best AI tip from the conversation: let the model use its own judgment about how to do work, rather than dictating every step.

## The example
You can tell Fable "only use automated testing for larger features, don't update and run tests for small copy or design changes" — but it's better to just tell Fable to use its own judgement when deciding to write tests.

Jesse Vincent added a related tip: tell Fable to use other models for smaller tasks, applying its own judgement about which model to use.

## Simon's memory
Simon prompted Claude Code:
> "For all coding tasks use your judgement to decide an appropriate lower power model and run that in a subagent"

Claude saved this as a memory file in `~/.claude/projects/name-of-project/memory/delegate-coding-to-subagents.md`. The system:
- Sonnet for substantive implementation
- Haiku for trivial/mechanical edits
- Self-contained prompt per delegation
- Review in the main loop before committing
- Design/audit/synthesis stay in the main model

> "So far it seems to be working well. I'm getting a ton of work done and my Fable allowance is shrinking less quickly than before."

## Notas e Conexões
- Direct companion to [[Stratechery-A Script for Mark Zuckerberg]] (same "route by task type" model)
- Pairs with [[TLDR AI-Amazon's Starlink rival Nvidia revenue share agentic autonomy levels]]'s "Agentic Autonomy Levels" (the broader pattern)
- The "judgment > rigid rules" framing is a useful AI-workflow heuristic
