---
title: llm-anthropic 0.26
source: Simon Willison
date: 2026-08-04
url: https://simonwillison.net/2026/Aug/4/llm-anthropic/#atom-everything
---

# llm-anthropic 0.26

- **Fonte:** Simon Willison
- **Data:** 2026-08-04
- **URL:** https://simonwillison.net/2026/Aug/4/llm-anthropic/#atom-everything

## Resumo / notas principais

Release: llm-anthropic 0.26 Simon Willison’s Weblog Subscribe Sponsored by: Dynatrace — When agents enter the SDLC, observability becomes the enabler to move from code generation to scalable engineering. Read the blog for a framework to get started 4th August 2026 Release llm-anthropic 0.26 — LLM access to models by Anthropic, including the Claude series Includes new features enabled by LLM 0.32 : New models: claude-fable-5 , claude-sonnet-5 , and claude-opus-5 . #75 , #76 Added server-side tools for WebSearch , WebFetch , CodeExecution , and AnthropicMCP , available through LLM's -T interface or Python tools= . The previous -o web_search* options have been removed in favor of -T WebSearch . #79 Upgraded to llm>=0.32 . Reasoning, tool calls, tool results, and server-side tool results now stream as typed events. Reasoning for llm CLI prompts now displays to standard error unless you pass --hide-reasoning/-R . Simplified extended thinking to thinking and thinking_effort ( low , medium , high , xhigh , or max ). Claude 5 models think by default; -o thinking 0 disables thinking for Sonnet 5 and Opus 5, while Fable 5 always thinks. -R/--hide-reasoning now omits reasoning from responses 
