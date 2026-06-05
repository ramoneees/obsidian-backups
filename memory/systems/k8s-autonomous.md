# Kubernetes Autonomous Alert System

## Infrastructure

| Component | Version/Detail |
|-----------|---------------|
| Cluster | k3s v1.34.5 |
| Nodes | homeserver, olympus |
| API | https://192.168.50.10:6443 |
| Auth | configmaps/secrets |

## Alert Flow

```
Alertmanager
    → n8n (auth: IH9hlXFpXJ6WL1nO)
    → Hermes webhook (k8s-alerts, secret: DL0OTiNxYOtFbkF19rRm3lu7TE6MIdDKFsQZhmmo9H0)
    → Notify Hermes (auth: D1X5OyGlkuo7UwdR)
    → Telegram group (-5143983732)
```

## Webhook Payload

Hermes webhook expects:
```json
{
  "message": "alert description",
  "url": "link to alert",
  "secret": "DL0OTiNxYOtFbkF19rRm3lu7TE6MIdDKFsQZhmmo9H0"
}
```

## Auto-Response Actions

Hermes can execute:
- `kubectl restart` — restart failing pods
- `kubectl scale` — scale deployments
- `kubectl delete` — remove stuck resources

## Related

- [[../sessions/2026-05-14]] — Last setup session
- [[hermes-agent]] — Hermes core config