---
title: "PostgreSQL 19 Released"
source: https://simonwillison.net/2026/Nov/19/postgresql-19/
date: 2026-11-20
tags: [postgres, devops, replicacao, ia]
---

PostgreSQL 19 saiu — dois meses atrasado em relação ao calendário tradicional de setembro, e o motivo é um retrato dos tempos: o time precisou lidar com a enxurrada de relatórios de vulnerabilidade gerados por IA, a "apocalipse de vulnerabilidades reportadas por IA" em curso. Bots reportam CVEs em volume industrial; humanos filtram. O release valeu a espera.

A feature estrela é o comando WAIT FOR LSN: consistência read-your-writes entre primário e standbys, nativa. A aplicação grava no primário, captura o LSN (log sequence number) via pg_current_wal_insert_lsn(), guarda esse valor — um cookie assinado resolve — e, na requisição seguinte, a sessão na réplica roda WAIT FOR LSN para esperar a réplica alcançar aquele ponto do WAL antes de ler. Com timeout opcional, aliás, para não travar a aplicação se a réplica atrasar.

O padrão não é novo: a Wikipédia roda uma versão artesanal disso sobre replicação MySQL há anos, guardando a posição do binlog na sessão e esperando a réplica alcançá-la no início de cada request. O MySQL tem o equivalente (WAIT_FOR_EXECUTED_GTID_SET). A novidade é isso virar SQL nativo do Postgres em vez de hack de aplicação.

Duas provocações ficam: infraestrutura crítica agora tem ciclo de release moldado por relatórios gerados por máquina; e padrões que eram mote de hiperscaler viraram quatro linhas de SQL para qualquer mortal. Réplica de leitura deixou de exigir middleware de consistência.

## Por que importa

- O VPS roda postgres:18 e o precisase usa PG16 — PG19 é o alvo natural da próxima migração, e WAIT FOR LSN é feature concreta que justifica o upgrade.
- Se o k3s/Olympus um dia precisar de réplicas de leitura, read-your-writes nativo mata uma classe inteira de bugs de consistência sem camada extra.
- A "AI-reported vulnerability apocalypse" é o cruzamento AI×devops do momento — vale calibrar o tratamento de relatórios de segurança automatizados no pipeline do homelab.

## Frases notáveis

> "A session on a standby can use WAIT FOR LSN to wait until the standby has replayed the write-ahead log (WAL) up to a specific log sequence number (LSN) before running a query, so the application can read data it just wrote on the primary."

> "This year's release came two months later thanks mainly to the flurry of issues that the PostgreSQL team needed to address as part of the ongoing AI-reported vulnerability apocalypse."
