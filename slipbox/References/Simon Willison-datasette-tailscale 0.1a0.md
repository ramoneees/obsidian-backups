---
title: "datasette-tailscale 0.1a0"
source: "Simon Willison's Weblog"
date: 2026-06-17
url: https://simonwillison.net/2026/Jun/16/datasette-tailscale/
author: "Simon Willison"
category: "Release Notes"
tags: [datasette, tailscale, plugin, networking, simon-willison, data-tools, vpn]
ingested: 2026-06-17
---

# datasette-tailscale 0.1a0

## Fonte
Simon Willison's Weblog (Release)

## Data
2026-06-17 (publicado 16 Jun 16:18)

## URL
https://simonwillison.net/2026/Jun/16/datasette-tailscale/

## Resumo

Plugin experimental alpha pra Datasette: `datasette-tailscale` — roda Datasette numa rede Tailscale.

**Como usar:**

```bash
datasette tailscale mydata.db \
  --ts-authkey tskey-auth-xxxx --ts-hostname datasette-preview
```

Inicia um servidor Datasette localhost com um **sidecar Tailscale** que conecta à sua Tailnet, de modo que `http://datasette-preview/` serve o Datasette.

**Implementação:** usa os Python bindings da biblioteca experimental [[tailscale-rs]]. Willison [registrou uma issue](https://github.com/tailscale/tailscale-rs/issues/243) perguntando se há um jeito mais limpo de configurar o mecanismo de proxy.

**Status:** alpha muito experimental. Não é pra uso em produção ainda.

## Recursos

- [Release 0.1a0 no GitHub](https://github.com/datasette/datasette-tailscale/releases/tag/0.1a0)
- [Tailscale](https://tailscale.com/) — serviço de VPN mesh

## Notas e Conexões

- Combinação poderosa: Datasette (SQLite + UI web) + Tailscale (rede privada sem abrir portas) = banco de dados publicável de forma segura, sem deploy em servidor público.
- Caso de uso claro: **preview de dados pra clientes ou equipe sem deploy público**. Cada instância na Tailnet.
- Conecta com [[datasette 1.0a34]] (lançado mesmo dia).
- Tailscale tem sido adotado amplamente por developers pra expor serviços locais a times remotos.
