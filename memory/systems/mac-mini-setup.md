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
## Session 2026-08-02 (cont.)

### CouchDB abandoned

- Cron `CouchDB Memory Sync` (id 41cb37c0b2c4): disabled in jobs.json
- Scripts removed from `~/.hermes/scripts/`, `~/.hermes/profiles/{crisp,nina}/scripts/`
- CouchDB credentials cleaned (was hardcoded in `couchdb-memory-sync.py`)
- Skill `obsidian-hermes-integration`'s `couchdb-livesync-writer.py` removed (depended on script)

### Gateway main launched

- Created `~/Library/LaunchAgents/ai.hermes.gateway-main.plist`
- Loaded via `launchctl load` — runs at boot, restart on crash
- WorkingDirectory + HERMES_HOME = `/Users/ramoneees/.hermes` (default profile, no `--profile` flag)
- Telegram polling: OK (bot Jarvis, fallback IPs via DNS-over-HTTPS)
- Webhook 8644: OK (k8s-alerts, n8n-complete routes)
- Mattermost: failing ("No route to host" to `chat.ramoneees.com`) — DNS não resolve, sem VPN antiga
- Api_Server 8642: port conflict com `hermes serve` PID 8898 (esperado)
- WhatsApp: disabled (`WHATSAPP_ENABLED=false`) — Nina profile has its own WhatsApp via Baileys

### Cron pipeline overview (15 jobs, 1 OFF)

Loop Obsidian (7 jobs):
- Daily Note (07:00) → daily-note.py
- Weekly Review (dom 20:00) → weekly-review.py
- Content Ingestion (18:00) → RSS scan + ingest
- Obsidian Vault — Git Auto-Sync (every 30m) → obsidian-git-sync.py → GitHub
- Daily Note — Session Summary (23:00)
- Couple 7-min Daily Check-in (07:00) → Telegram
- (CouchDB Memory Sync REMOVED)

Briefings (3 jobs):
- Briefing Diário (07:00) → Telegram
- weekly-agenda-briefing (dom 20:00) → Telegram
- Futebol Europeu Semanal (seg 09:00) → Telegram

Personal (3 jobs):
- Sprint Planning Prep (qua 20:00)
- Leitura do Dia (12:00) → Telegram
- hermes-state-monthly-sync (dia 1, 09:00)

Finance (2 jobs):
- Firefly Lunch Flow daily sync (01:00)
- Firefly AI categorizer daily (01:15)

### Pending issues

- Couple Check-in cron has `workdir: /home/ramoneees/obsidian-vault` (Linux path). Agent may write to wrong location. Fix: `hermes cron edit` or update jobs.json `workdir` to `/Users/ramoneees/obsidian-vault`.
- `chat.ramoneees.com` (Mattermost) unreachable — DNS doesn't resolve from Mac. Probably needs VPN or domain DNS fix.
- scripts em `~/.hermes/scripts/` têm cópias em `profiles/{crisp,nina}/scripts/` — duplicação. Investigar se é via symlink ou cópia real.
