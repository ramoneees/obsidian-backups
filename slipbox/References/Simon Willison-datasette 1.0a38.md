---
title: datasette 1.0a38
source: Simon Willison
date: 2026-08-06
url: https://simonwillison.net/2026/Aug/6/datasette/#atom-everything
---

# datasette 1.0a38

- **Fonte:** Simon Willison
- **Data:** 2026-08-06
- **URL:** https://simonwillison.net/2026/Aug/6/datasette/#atom-everything

## Resumo / notas principais

Release: datasette 1.0a38 Simon Willison’s Weblog Subscribe Sponsored by: Dynatrace — When agents enter the SDLC, observability becomes the enabler to move from code generation to scalable engineering. Read the blog for a framework to get started 6th August 2026 Release datasette 1.0a38 — An open source multi-tool for exploring and publishing data This release fixes a SQL injection security issue that affects Datasette instances that serve a mixture of public and private tables in the same database, with access configured using the Datasette permissions system . Site administrators who serve private tables in this way are advised to disable the execute-sql permission ` on that database to prevent users from accessing private tables using raw SQL queries. The bug that has been fixed would have allowed users with access to any public table to execute SQL injection attacks despite that restriction, giving them read-only access to data in private tables in the same database. This fix is also available in Datasette 0.65.3 . Thankfully this particular configuration - private tables and public tables exposed for the same database within the same instance - is likely to be rare. I've not e
