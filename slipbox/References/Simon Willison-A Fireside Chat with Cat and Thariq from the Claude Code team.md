---
source: Simon Willison
title: "A Fireside Chat with Cat and Thariq from the Claude Code team"
date: 2026-07-21
url: https://simonwillison.net/2026/Jul/21/cat-and-thariq/
author: Simon Willison (annotated talk transcript)
category: AI Engineering / Anthropic / Claude Code
tags: [anthropic, claude-code, claude-tag, claude-fable, coding-agents, evals, simon-willison, annotated-talk]
ingested: 2026-07-21
blogwatcher_id: 1294
---

# A Fireside Chat with Cat and Thariq from the Claude Code team

**Source**: Simon Willison's Weblog (annotated transcript of talk)
**Date**: 2026-07-21 12:54 UTC
**URL**: https://simonwillison.net/2026/Jul/21/cat-and-thariq/
**Original venue**: AI Engineer World's Fair, 2026
**Speakers**: Simon Willison (host), Cat Wu & Thariq Shihipar (Anthropic's Claude Code team)
**Video**: [youtube.com/watch?v=uU5Gv2h8-9g](https://www.youtube.com/watch?v=uU5Gv2h8-9g)

## TL;DR

An annotated transcript of a fireside chat at AI Engineer World's Fair 2026. The Claude Code team discusses Claude Tag, Claude Fable, coding-agent security, evals, and how Anthropic uses these tools themselves. Top-level news: Claude Tag now lands 65% of product-engineering PRs for the Claude Code team. The Claude Code system prompt recently dropped 80% in size — adding examples is "no longer best practice" for Fable 5 / Opus 4.8.

## Top-Level Highlights (Simon's bolded points)

- **Claude Tag** (Claude's new collaborative Slack integration) now lands **65% of the product engineering PRs** for the Claude Code team.
- **Claude Code ships features to Anthropic employees first**, and only ships the features that demonstrate user retention with that cohort.
- Critical changes to Claude Code are still reviewed manually, but the team increasingly relies on automated code review for the "outer layers."
- **Adding examples to a system prompt is no longer best practice** for models like Fable 5 or even Opus 4.8. The Claude Code system prompt recently **reduced in size by 80%**.
- Lists of "don't do X and don't do Y" can reduce the quality of results from the latest models.
- [Dogfooding](https://en.wikipedia.org/wiki/Eating_your_own_dog_food) inside Anthropic is called **"ant fooding"**.
- Anthropic **really believes in their [auto mode](https://code.claude.com/docs/en/auto-mode-config)**, sees it as an enabling technology for Claude Tag.
- Thariq advises offsetting coding-agent-induced Deep Blue by "being more ambitious" with the work you take on.
- **Fable is competent at editing video**; Thariq [used it](https://twitter.com/trq212/status/2064826394589442448) to edit its own launch video.
- Anthropic's culture of working (internally) in public is key to their success — demonstrated by the way they use Claude Tag in their public Slack Channels.

## Selected Quotes

### Cat Wu on the year since Sonnet 3.7

> "When we first came out with Claude Code and Sonnet 3.7, you would give it a task and you would have to closely monitor every single little thing it tried to do. I would read every permission prompt extremely carefully. I would frequently say no — no, no, no, did you check this file? Did you check that file? And now it's been incredible with every model generation. We've all gotten a chance to take a step back and delegate a lot more of the menial implementation to Claude. It's freed up a lot of our time to think about more creative work... And now with Fable it's a totally different step change improvement. For a lot of our use cases you can actually one-shot a ton of features with Fable now."

### Thariq on the higher-quality-work imperative

> "We have to do higher quality work than we've ever done before. The outputs are incredibly high quality. I've been using it to edit videos a bunch, and I'm like, okay, it has to meet the very exacting demands of our brand team in a couple of hours or we just can't do it. That's how I'm trying to shift with Fable: the best work we've ever done, faster than we've ever done it before."

### Conventional software engineering no longer holding

Simon: "What's a piece of conventional software engineering that was true a year ago that you don't think holds anymore?"

(Cat + Thariq respond — full transcript at original URL.)

## Por que isso me interessa

The "system prompt shrank 80%" and "adding examples is no longer best practice" are non-obvious signals about how the latest Claude models behave. Worth updating any prompt-engineering heuristics that assumed more context = better results. The Claude Tag + 65% PRs number is a concrete data point on what in-house AI adoption looks like at the frontier labs.

## Notas e Conexões

- [[Nativ: Run AI models locally on your Mac]] — same-day SW link
- [[Reverse-engineering is cheap now]] — same-day SW link
- Adjacent: TGC's [[AI and Formation How Does AI Shape Our Loves]] — same day, on the formation cost of frictionless coding agents
- Adjacent: AE's [[How to Plan Deep Work Sessions With Claude]] — same day, on using Claude for planning (assumes Claude Code-style workflows)

---

**Video**: [Claude Fable, Claude Tag, and Anthropic's Culture — Cat Wu & Thariq Shihipar ft Simon Willison](https://www.youtube.com/watch?v=uU5Gv2h8-9g) — AI Engineer YouTube channel.

**Tags** (from Simon's weblog): anthropic, claude-code, claude-tag, claude-fable, coding-agents, annotated-talks.