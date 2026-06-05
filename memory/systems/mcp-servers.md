# MCP Servers — mcporter CLI Reference

## Quick Reference

All 18 MCP servers accessed via `mcporter` CLI. No native MCP tools in config.yaml (mcp_servers: {}).

## Commands

```bash
# List servers
mcporter list

# Call tool
mcporter call <server> <tool> [--args <json>]

# Add server
mcporter config add <server> <url>

# Remove server
mcporter config remove <server>
```

## Config Location

`/home/ramoneees/config/mcporter.json` — Contains all tokens and server URLs

## Server List

| Server | Purpose | Token Location |
|--------|---------|----------------|
| minimax | TTS, Music, Video, Image | mcporter.json |
| ticktick | Task management | mcporter.json |
| (16 more) | Various integrations | mcporter.json |

## n8n Integration

For n8n MCP calls: Python subprocess + `--args` flag + JSON payload
See [[n8n-workflows]]

## Related

- [[hermes-agent]] — Core config
- [[minimax-mcp]] — MiniMax specific setup