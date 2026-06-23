---
source: Simon Willison
title: "sqlite-utils 4.0rc1 adds migrations and nested transactions"
url: https://simonwillison.net/2026/Jun/21/sqlite-utils-40rc1/
published: 2026-06-21
category: Release
tags: [sqlite-utils, sqlite, python, migrations, transactions, release]
ingested: 2026-06-23
---

# sqlite-utils 4.0rc1 adds migrations and nested transactions

[sqlite-utils](https://sqlite-utils.datasette.io/en/latest/) é a biblioteca + CLI Python do Simon para trabalhar com SQLite. O primeiro release candidate da v4 está aberto para teste antes do stable.

## Duas Novidades Principais

### 1. Migrations

Port modificado do pacote `sqlite-migrate` (que já provou-se ao longo de anos no LLM e outros projetos). Sistema deliberadamente pequeno: **não há reverse migrations** — erros devem ser corrigidos deployando uma nova migration que desfaz.

```python
from sqlite_utils import Database, Migrations

migrations = Migrations("creatures")

@migrations()
def create_table(db):
    db["creatures"].create({"id": int, "name": str, "species": str}, pk="id")

@migrations()
def add_weight(db):
    db["creatures"].add_column("weight", float)
```

Uso via Python (`migrations.apply(db)`) ou CLI (`sqlite-utils migrate creatures.db migrations.py`).

### 2. `db.atomic()` Transactions

Antes: `with db.conn:` (wrapper fino sobre o sqlite3 do Python). Agora, abstração para transações aninhadas via savepoints, inspirado na nomenclatura de Django e Peewee:

```python
with db.atomic():
    db.table("dogs").insert({"id": 1, "name": "Cleo"}, pk="id")
    try:
        with db.atomic():
            db.table("dogs").insert({"id": 2, "name": "Pancakes"})
            raise ValueError("skip this one")
    except ValueError:
        pass
    db.table("dogs").insert({"id": 3, "name": "Marnie"})
```

## Mudanças Incompatíveis

- Upserts agora usam `INSERT ... ON CONFLICT SET` em SQLite > 3.23.1 (sutil breaking change vs o `INSERT OR IGNORE` + `UPDATE` anterior). Opt-in via `use_old_upsert=True`.
- Drop Python 3.8, suporte a Python 3.13.

## Notas e Conexões

- [[Simon Willison]] — fonte.
- Tag: sqlite-utils.
- Companion release note: [[Simon Willison-Release: sqlite-utils 4.0rc1]].
