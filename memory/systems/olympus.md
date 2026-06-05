# Olympus — Kubernetes Cluster

## Infrastructure

| Component | Detail |
|-----------|--------|
| Engine | k3s v1.34.5 |
| Nodes | homeserver, olympus (both amd64) |
| API | https://192.168.50.10:6443 |

## Alert Pipeline

```
Alertmanager → n8n → Hermes → Telegram (-5143983732)
```

Detalhes completos: [[k8s-autonomous]]

## Git Access

- Gitea token auth **quebrado** — usar git CLI com embedded creds
- Clone: `git clone "https://prometheus:<password>@git.ramoneees.com/ramoneees/olympus.git" /tmp/olympus`
- Creds: ver [[../secrets]]

## Related

- [[k8s-autonomous]] — Alert system detalhado
- [[hermes-agent]] — Hermes config
- [[../secrets]] — Credenciais
