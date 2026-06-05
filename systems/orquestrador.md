# Orquestrador — Multi-Agent Orchestrator

## Overview

Multi-agent delegation system via `delegate_task` tool. Routes work to specialized agents based on toolsets.

## Config

**Location**: `~/.hermes/config.yaml`

## Toolsets (5 total)

| Toolset | Purpose |
|---------|---------|
| financeiro | Financial operations, invoicing, reconciliation |
| gtd | Task management, planning, execution |
| devops | Infrastructure, K8s, deployments |
| pesquisa | Research, web search, information gathering |
| automacao | n8n workflows, integrations, automation |

## Usage

```python
delegate_task(
    goal="specific task description",
    toolsets=["financeiro"],  # or ["gtd", "devops"]
    context="relevant background info"
)
```

## Patterns

- Batch mode: up to 3 parallel tasks with `tasks=[]`
- Subagents are leaf by default (can't delegate further)
- Orchestrator mode: can spawn workers (disabled by default)

## Related

- [[hermes-agent]] — Core agent setup
- [[ticktick-config]] — GTD integration