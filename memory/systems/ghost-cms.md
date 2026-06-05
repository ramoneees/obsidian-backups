# Ghost CMS — Olaria do Pensamento

## Overview

Blog pessoal hospedado em me.ramoneees.com via k3s (nameserver apps).

## Setup

| Component | Detail |
|-----------|--------|
| URL | me.ramoneees.com |
| Theme | Solo (customizado) |
| Palette | Olaria — CSS injetado em `default.hbs` após `{{ghost_head}}` |
| CSS | Todas as vars com `!important` |
| Hosting | k3s cluster (Olympus) |
| Content language | PT-BR, conversational |

## Newsletter

- Nome: "Olaria do Pensamento"
- Sender: Ramon Rios

## Tags

Filosofia, Teologia, Cultura Pop, Crônica, Podcast, Tecnologia, Arte

## API Limitations

- Admin API **não** tem permissão de settings
- Para settings: usar MariaDB direto (database: `mariadb.databases`)
- Keys: ver [[../secrets]]

## Skill

Hermes skill: `ghost-manager` — criar/editar/publicar posts.

## Related

- [[../secrets]] — API keys e credenciais
- [[hermes-agent]] — Hermes core config
