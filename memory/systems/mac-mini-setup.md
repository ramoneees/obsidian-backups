# Mac Mini Setup (2026-08-02)

Migration state from Linux → Mac Mini (Apple Silicon, macOS 26.6).

## Working

- ripgrep: `brew install ripgrep` ✓
- Toolsets ativos: stt, computer_use, video, spotify (além dos default)
- 22 toolsets habilitados, 135 skills, 905 sessões históricas preservadas
- Gateways: main=8642/8644, crisp=8643/8645, nina=8646/8647 — todos healthy
- LiteLLM proxy 10.43.227.167:4000 funcionando

## Needs attention

### Docker via OrbStack

- OrbStack.app em /Applications (NÃO Docker Desktop — escolha consciente pra Apple Silicon)
- `orb` e `orbctl` em /opt/homebrew/bin
- `docker` CLI só funciona após daemon subir (`orbctl start` ou abrir app)
- **First start trava**: popup do macOS pedindo permissão pra instalar Rosetta 2
  - Bloqueio GUI — terminal não consegue resolver, user precisa aceitar manualmente
  - OrbStack Helper abre "Rosetta 2 Updater.app" automaticamente
  - Após aceitar, daemon sobe em ~10s e `docker` aparece no PATH

### state.db "I/O error" warning

- False positive. Gateway serve (PID ~8898) segura lock exclusivo via WAL
- DB íntegro: 905 sessões, 51 tabelas, FTS5 completo
- Pra inspecionar manualmente: `cp ~/.hermes/state.db* /tmp/copy.db && sqlite3 /tmp/copy.db`
- Ou consultar via gateway API (sessões rodando)

### MCP servers

- `mcp_servers: {}` no config.yaml — zero configurados
- Se user tinha algum no Linux, precisa registrar manualmente (nome + endpoint/command)

## Tools status (hermes doctor)

WARN (irrelevantes):
- Nous Portal / OpenAI Codex / xAI OAuth não logados (provider é custom LiteLLM)
- discord.py não instalado (não usamos Discord)
- GITHUB_TOKEN ausente (só limita rate do skills hub)
- Anthropic API "couldn't verify" (provider custom mascara, OK)

OK após setup:
- ripgrep (era warning, agora ✓)
- stt, computer_use, video, spotify (foram ativados nesta sessão)