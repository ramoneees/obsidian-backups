---
title: New release of LLM adds support for reasoning traces, OpenAI Responses, server-side tools, and smarter logging
source: Simon Willison
date: 2026-08-04
url: https://simonwillison.net/2026/Aug/4/new-release-of-llm/#atom-everything
---

# New release of LLM adds support for reasoning traces, OpenAI Responses, server-side tools, and smarter logging

- **Fonte:** Simon Willison
- **Data:** 2026-08-04
- **URL:** https://simonwillison.net/2026/Aug/4/new-release-of-llm/#atom-everything

## Resumo / notas principais

New release of LLM adds support for reasoning traces, OpenAI Responses, server-side tools, and smarter logging Simon Willison’s Weblog Subscribe Sponsored by: Dynatrace — When agents enter the SDLC, observability becomes the enabler to move from code generation to scalable engineering. Read the blog for a framework to get started New release of LLM adds support for reasoning traces, OpenAI Responses, server-side tools, and smarter logging 4th August 2026 I released LLM 0.32 this morning, the most significant new version of LLM since the initial launch of the project. The new version includes support for visible reasoning traces, server-side provider tools, redesigned content-addressable SQLite logs, new models, and new features enabled by the OpenAI Responses API. I also released a new version of the llm-anthropic plugin with substantial updates of its own. Headline features for LLM CLI users Running LLM against reasoning models now displays their reasoning traces to standard error, so you can see what they are “thinking” without that information being included in the standard output that you might pipe to another tool. Add -R/--hide-reasoning to turn this off. LLM includes support
