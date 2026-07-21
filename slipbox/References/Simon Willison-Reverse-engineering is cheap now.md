---
source: Simon Willison
title: "Reverse-engineering is cheap now"
date: 2026-07-20
url: https://simonwillison.net/2026/Jul/20/cheap-reverse-engineering/
author: Simon Willison (note)
category: AI / Coding Agents / Home Automation
tags: [reverse-engineering, coding-agents, home-automation, llms, simon-willison]
ingested: 2026-07-21
blogwatcher_id: 1295
---

# Reverse-engineering is cheap now

**Source**: Simon Willison's Weblog
**Date**: 2026-07-20 19:24 UTC
**URL**: https://simonwillison.net/2026/Jul/20/cheap-reverse-engineering/

## TL;DR

Coding agents changed the economics of reverse-engineering home devices. The technical possibility was always there — what changed is the ROI: when the initial effort is cheap, the "what if the undocumented API breaks next year?" risk stops being a blocker. The code is cheap enough that maintaining it (or throwing it away and starting again) carries no psychological baggage.

## Full Text (short note)

> I keep hearing anecdotes from people who used coding agents to reverse-engineer and automate devices in their homes.
>
> I think this is an interesting illustration of the impact of the reduced cost of writing code.
>
> Prior to agents, it was entirely possible to reverse-engineer home devices. The problem was the ROI — was it really worth all of that effort? More importantly, any experienced programmer knows that undocumented, unstable APIs like that may well change or break in the future. Is that initial work worth the effort if you're committing yourself to a frustrating cycle of maintenance in the future?
>
> Coding agents change that equation entirely. The effort to get a simple automation working has dropped, as has the cost of trying and failing to get it to work. Since the code is so cheap, the idea of having to maintain it in the future — or throw it away and start again — carries way less psychological baggage.

## Por que isso me interessa

The thesis is a clean economic argument, not a technical one. The "psychological baggage" framing is the under-appreciated lever — most home-automation projects don't die because of complexity, they die because the long tail of maintenance isn't worth the upfront cost. Coding agents change the maintenance cost enough that the long tail stops mattering.

## Notas e Conexões

- Same-day SW: [[Nativ Run AI models locally on your Mac]] — on the tooling layer that enables cheap coding-agent workflows
- Same-day SW: [[A Fireside Chat with Cat and Thariq from the Claude Code team]] — on the in-house culture of using these agents at Anthropic
- Adjacent: TGC's [[AI and Formation How Does AI Shape Our Loves]] — Keller's "appearance of depth without the cost" critique maps onto this same dynamic (cheap code → cheap value?)

---

**Tags** (from Simon's weblog): reverse-engineering, ai, generative-ai, llms, ai-assisted-programming, coding-agents.