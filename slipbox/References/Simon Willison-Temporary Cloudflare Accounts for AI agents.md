---
source: Simon Willison
title: "Temporary Cloudflare Accounts for AI agents"
url: https://blog.cloudflare.com/temporary-accounts/
published: 2026-06-21
category: Cloud Infrastructure
tags: [cloudflare, workers, ai-agents, serverless, deployment]
ingested: 2026-06-23
---

# Temporary Cloudflare Accounts for AI agents

Link post. O anúncio diz "for AI agents" mas — como tem sido comum — o gancho em AI não é necessário, é um recurso interessante para qualquer pessoa.

## TL;DR

Você pode criar um projeto Cloudflare Workers e fazer deploy **sem criar conta Cloudflare**:

```
npx wrangler deploy --temporary
```

Cloudflare faz deploy em um novo projeto efêmero que fica no ar por **60 minutos**. O terminal cospe uma URL para "reivindicar" o projeto se quiser que dure mais.

## Validação por Simon

Testou com GPT-5.5 xhigh no Codex Desktop construindo `simonw/cloudflare-redirect-resolver` (tool para seguir redirects HTTP e retornar o destino final). O deployment temporário funcionou como anunciado.

> The "AI hook isn't really necessary" — esse padrão se repete em vários anúncios recentes.

## Notas e Conexões

- [[Simon Willison]] — fonte.
- Tag: cloudflare.
