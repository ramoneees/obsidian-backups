---
title: condense-json 1.1
source: Simon Willison
date: 2026-08-03
url: https://simonwillison.net/2026/Aug/3/condense-json/#atom-everything
---

# condense-json 1.1

- **Fonte:** Simon Willison
- **Data:** 2026-08-03
- **URL:** https://simonwillison.net/2026/Aug/3/condense-json/#atom-everything

## Resumo / notas principais

Release: condense-json 1.1 Simon Willison’s Weblog Subscribe Sponsored by: Dynatrace — When agents enter the SDLC, observability becomes the enabler to move from code generation to scalable engineering. Read the blog for a framework to get started 3rd August 2026 Release condense-json 1.1 — Python function for condensing JSON using replacement strings After shipping condense-json 1.0 I started integrating it into LLM, and found there were some desirable new features already: Replacements object can now include values other than strings. These will be identified and used as structural replacements by condense_json() and uncondense_json() . #8 Objects can be used as the basis for merge operations. condense_json() will identify if there are objects that are a close match and will store instructions for keys to update or delete. uncondense_json() can then apply these merges. I also added some round-trip tests using the Hypothesis property-based Python testing library. Posted 3rd August 2026 at 4:56 am Recent articles Now we have a timeline of the OpenAI accidental attack against Hugging Face - 7th August 2026 One-shotting a Raccoon Heist game using Claude Fable 5 - 5th August 2026 New 
