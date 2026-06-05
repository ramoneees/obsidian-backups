# Contabilidade — Finance Flow

## Setup

**Manager.io**
- URL: https://manager.octacode.pt
- User: ramonp.rios@gmail.com

## Monthly Flow (Dia 10)

```
1. Email faturas arrives (30d terms)
2. n8n workflow:
   - Reads emails → extracts attachments
   - Saves to GDrive (Faturas 2026 folder)
   - Uploads to Manager.io
3. Manager.io processes for accounting
```

## Key Notes

- 30-day payment terms standard
- Monthly cycle: receive → organize → upload
- Check Manager.io for reconciliation status

## Related

- [[../systems/n8n-workflows]] — n8n automation details