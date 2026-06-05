# Hermes Agent — Full Config Reference

## Core Setup

| Setting | Value |
|---------|-------|
| Model | glm-5-turbo |
| Provider | LiteLLM Proxy |
| Endpoint | http://10.43.227.167:4000 |

## Memory System

**Capacity**: 2,200 chars (compact by design)
**Storage**: `~/.hermes/memory.json`
**Target**: Durable facts, user preferences, environment facts

### Current Memory Entries (11 entries, 96% full)

```
MCP servers: all via mcporter CLI (18 servers)
Telegram: bot @RamoneeesHermesBot, chat ID 8257687396
Contabilidade: Manager.io (manager.octacode.pt), fluxo faturas 30d
Obsidian vault: /home/ramoneees/obsidian-vault, CouchDB (ramoneees)
K8s: k3s v1.34.5, homeserver+olympus, API 192.168.50.10:6443
TickTick: Finanças project ID 69ecc8f78f0864e5892f95f2
MiniMax MCP: speech-2.8-hd, music-2.6, video Hailuo-2.3, image-01
n8n mcporter calls: Python subprocess + --args flag
Orquestrador: 5 toolsets via delegate_task
```

### Memory Rules
- No task progress or session logs
- No PR numbers, commit SHAs, issue numbers
- Stable facts only — stale in 1 week = not saved
- Preferences and corrections > environment > procedural

## Skills

Skills live in `~/.hermes/skills/`. Categories:
- `biweekly-planning/`, `creative/`, `data-science/`, `devops/`
- `email/`, `financeiro/`, `github/`, `gaming/`, `leisure/`
- `media/`, `mlops/`, `note-taking/`, `pdf-to-base64-vision/`
- `productivity/`, `red-teaming/`, `research/`, `smart-home/`
- `social-media/`, `software-development/`, `ticktick-api/`
- `time-tracking-4mation/`, `yuanbao/`

## Skills Loading Pattern

When answering, scan skills list first. If match, load with `skill_view(name)`. Always load for:
- Configuring/using Hermes itself → load `hermes-agent` skill first
- MCP tools → load `mcporter` skill
- TickTick → load `ticktick-api` skill
- GitHub → load relevant github-* skill

## Cron Jobs

Cron jobs saved to `~/.hermes/crons/`. Manage with `cronjob` tool.

## Orquestrador

Multi-agent orchestrator via `delegate_task`. Config: `~/.hermes/config.yaml`

**Toolsets**: financeiro, gtd, devops, pesquisa, automacao

## Related

- [[../people/ramon]] — User profile
- [[../sessions/2026-05-14]] — Memory sync session
- [[mcp-servers]] — MCP configuration details
- [[k8s-autonomous]] — Kubernetes alert workflow