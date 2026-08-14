# Dev Environment (Mac mini M4) — 2026-08-14

## Layout
- `~/dev/<name>` — all agent code workspaces
- `mkdev <name> [python|node|static]` (at `~/.local/bin/mkdev`) — scaffolds git repo + AGENTS.md agent rules (guardrails: no rm -rf outside repo, no touching ~/.hermes or vault, tests before done, blocker protocol) + pyproject/pytest via uv
- Verified: testdrive project, pytest passes

## Toolchain
- Python: uv-managed 3.12 + 3.13 (+ system 3.9, 3.14). Never global pip.
- Lint/type: ruff, pyright, pre-commit (all `uv tool`, in ~/.local/bin)
- Node 26, bun; claude-code + codex casks (`/opt/homebrew/bin/claude`, `codex`)
- Git: user ramoneees / ramonp.rios@gmail.com, gh credential helper wired (https push works)
- SSH: no keys on this Mac yet — https+gh only

## Docker
- OrbStack. Auto-sleeps VM when idle (~0 cost when unused) — safe to leave installed; `orb start` if needed.
- Daemon verified 29.4.0 on 2026-08-14. Clean slate, no containers.

## macOS agent CLIs (all live)
- imsg (iMessage/SMS read+send) — Full Disk Access already granted
- remindctl (Reminders, full access via osascript prompt trick)
- memo (Apple Notes; account empty = "No notes found" is normal)

## Computer Use
- cua-driver at ~/.local/bin/cua-driver, daemon via CuaDriver.app, telemetry DISABLED
- Accessibility: granted. Screen Recording: was still pending 2026-08-14 — if false, toggle in System Settings > Privacy & Security > Screen Recording (CuaDriver), then `pkill -f CuaDriver` + relaunch `open -n -g -a CuaDriver --args serve --socket /Users/ramoneees/Library/Caches/cua-driver/cua-driver.sock`
- check: `cua-driver check_permissions | grep -E accessibility\|screen`

## Existing infra from Linux migration
- ~/.hermes/ORCHESTRATOR_GUIDE.md (PT) — specialist subagent delegation patterns
- kanban.db (tasks, task_runs, task_comments, task_links) — for long-running agent job tracking
- ~/.hermes/sandboxes/singularity — stale Linux entry
