---
source: Simon Willison
title: "Nativ: Run AI models locally on your Mac"
date: 2026-07-21
url: https://simonwillison.net/2026/Jul/21/nativ/
author: Simon Willison (link blog)
category: AI Tools / Local LLMs
tags: [macos, local-llms, mlx, prince-canuma, simon-willison, link-post]
ingested: 2026-07-21
blogwatcher_id: 1293
---

# Nativ: Run AI models locally on your Mac

**Source**: Simon Willison's Weblog (link blog)
**Date**: 2026-07-21 14:22 UTC
**URL**: https://simonwillison.net/2026/Jul/21/nativ/
**Format**: Link post (with Hacker News discussion linked)

## TL;DR

Prince Canuma (creator of the MLX-VLM Python library for running vision-LLMs on MLX) has shipped a new macOS desktop app called **Nativ** — wraps MLX in a full GUI with a chat interface + localhost API server (similar in shape to LM Studio). Notable: Nativ picked up MLX models that were already present in Simon's Hugging Face cache directory, which is the kind of detail that signals tight integration.

## Key Points

- **Author**: Prince Canuma — already known for [MLX-VLM](https://github.com/Blaizzy/mlx-vlm), the Python library for vision-LLMs on MLX.
- **What Nativ is**: macOS desktop application wrapping MLX. Provides chat UI + localhost API server (like LM Studio's shape).
- **Notable detail**: picked up MLX models Simon already had in his Hugging Face cache directory.
- **Hacker News discussion**: [news.ycombinator.com/item?id=48982681](https://news.ycombinator.com/item?id=48982681)

## Por que isso me interessa

Simon Willison's link blog is the highest-signal feed for "new local-LLM tooling dropped." Each entry is short but points to substantive new tools. Nativ is the latest in the LM-Studio-shaped category — desktop wrapper around a local model runtime with API server for downstream use.

## Notas e Conexões

- [[Reverse-engineering is cheap now]] — same-day SW link on the cost-of-coding-agents angle
- [[A Fireside Chat with Cat and Thariq from the Claude Code team]] — same-day SW link on Anthropic's coding-agent culture
- Simon's recent coverage of [MLX](https://simonwillison.net/tags/mlx/) and [local LLMs](https://simonwillison.net/tags/local-llms/)
- Hacker News discussion: [news.ycombinator.com/item?id=48982681](https://news.ycombinator.com/item?id=48982681)

---

**Simon Willison** is an independent AI researcher and blogger. Subscribe to his monthly briefing at [github.com/sponsors/simonw](https://github.com/sponsors/simonw).