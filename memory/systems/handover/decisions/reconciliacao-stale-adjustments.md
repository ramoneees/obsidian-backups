# Decisão: Reconciliação — deletar stale adjustments antes de postar nova

> Data: 2026-07-29. Origem: skill `lunchflow-open-banking-sync` § Idempotency patterns.

## O problema

O reconciliador cria uma transação `Reconciliação …` por dia, com `external_id = "lunchflow-reconcile:lf:<lfid>:<YYYY-MM-DD>"`. Isso é único-por-dia, então em princípio é idempotente — re-rodar não deveria duplicar.

**Mas** se o saldo real mudou entre runs (e.g. nova transação chegou entre o run 1 e o run 2), o `external_id` igual faz com que a API trate a nova tentativa como no-op, deixando o ajuste stale na conta. Resultado: a conta fica off-by-the-previous-adjustment-amount.

## A solução

Antes de postar a reconciliação de hoje:

```python
# 1. Procurar a reconciliação do mesmo dia
existing = find_transaction(
    account_id=account_id,
    external_id_prefix=f"lunchflow-reconcile:lf:{lf_id}:{today}",
)

# 2. Deletar se existir
if existing:
    delete_transaction(existing.gid)

# 3. Postar nova com o mesmo external_id único-por-dia
post_transaction(
    external_id=f"lunchflow-reconcile:lf:{lf_id}:{today}",
    ...
)
```

## Por que external_id não basta

External_id único-por-dia protege contra duplicação **literal** (mesmo ajuste postado 2x). Mas não protege contra **mudança de saldo** entre runs. A diferença entre runs é justamente o motivo de re-rodar.

## Por que não usar `POST /accounts/{id}/reconcile`

- A skill `firefly-iii-account-reconciliation` documenta que **alguns builds de Firefly retornam 404** nesse endpoint.
- O fallback com transação labeled é o que está implementado e funcionando.

## Não violar

Se você vir um run que cria `Reconciliação …` sem checar a antiga: **é bug, conserte**.
