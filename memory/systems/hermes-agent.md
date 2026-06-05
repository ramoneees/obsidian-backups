# Hermes Agent — Full Config Reference

## Core Setup

| Setting | Value |
|---------|-------|
| Model | glm-5-turbo |
| Provider | LiteLLM Proxy |
| Endpoint | http://10.43.227.167:4000 |

## Multi-Model Routing

| Role | Model | Notes |
|------|-------|-------|
| Main | glm-5-turbo | Default |
| auxiliary.vision | glm-5v-turbo | Vision tasks |
| compression | glm-4.7-flash | Free tier |
| session_search/title | glm-4.7-flash | Free tier |
| approval/mcp/skills_hub/flush | glm-4.7-flash | Free tier |
| web_extract/triage | glm-4.7-flashx | Free tier |
| curator | glm-5-turbo | Same as main |
| Delegation (personal group) | glm-5.1 / M2.7 / qwen3.6+ / ds-v4-pro | |
| Smart routing | Enabled | Simple queries → glm-4.7-flash |

### Specialized Toolsets

| Toolset | Model |
|---------|-------|
| coding | glm-5.1 |
| financeiro/administracao | M2.7 |
| agentico/pesquisa | qwen3.7-max |

## Memory System

**Capacity**: 2,200 chars (compact by design)
**Storage**: `~/.hermes/memory.json`
**Target**: Durable facts, user preferences, environment facts

### Memory Rules
- No task progress or session logs
- No PR numbers, commit SHAs, issue numbers
- Stable facts only — stale in 1 week = not saved
- Preferences and corrections > environment > procedural
- When approaching limit → offload details to Obsidian vault

## Obsidian Integration

- **Vault path**: `/home/ramoneees/obsidian-vault`
- **CouchDB LiveSync**: obsidian.ramoneees.com (user: ramoneees, pass: [[../secrets]])
- **DBs**: obsidian-notes, dailies, hermes
- **Cronjob**: syncs Hermes memories to CouchDB every 6h
  - Script: `couchdb-memory-sync.py`
  - Job ID: `41cb37c0b2c4`

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

## Telegram

- Bot: @RamoneeesHermesBot
- Chat ID: 8257687396
- WhatsApp: abandoned

## Related

- [[../people/ramon]] — User profile
- [[mcp-servers]] — MCP configuration details
- [[minimax-mcp]] — MiniMax specific setup
- [[n8n-workflows]] — n8n integration
- [[olympus]] — K8s cluster
- [[ghost-cms]] — Blog setup
- [[k8s-autonomous]] — Kubernetes alert workflow
- [[orquestrador]] — Delegation config
