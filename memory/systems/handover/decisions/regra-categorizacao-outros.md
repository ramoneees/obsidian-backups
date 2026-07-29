# Decisão: "Outros" é confirmation gate, não bucket final

> Data: 2026-07-29. Origem: skill `multi-currency-finance-reconciliation` § Categorization.

## Contexto

O categoriser tem um modelo de confiança de três outcomes:
- `CLASSIFIED` — alta confiança, padrão recorrente → aplica + persiste em memory
- `ASSUMED` — média confiança, plausível mas não verificado → aplica + persiste em memory
- `NEEDS_REVIEW` — baixa confiança, ou caiu em `Outros` → **enfileira, não aplica**

## Por que `Outros` não é resposta final

Se o categoriser chega em `Outros` para um comerciante novo, **NÃO auto-aplique** mesmo que o modelo retorne `CLASSIFIED`. Isso porque:

1. O usuário pediu explicitamente para ser **confrontado na primeira vez** que um comerciante novo aparece. `Outros` é exatamente o sinal "primeira vez".
2. Aplica-lo silenciosamente quebra o modelo de confiança: o "auto-aplicado" pareceria ter cobertura alta, mas estaria enchendo `Outros` sem que o usuário tivesse revisado.
3. O usuário **confia mais na fila de review** do que no contador de auto-aplicados. A fila é o sinal honesto.

## Implementação

```python
# Padrão correto (NÃO auto-aplica Outros)
if outcome == "CLASSIFIED" and category in KNOWN_CATEGORIES:
    apply(category)
    persist_to_memory(merchant, category)
elif outcome == "NEEDS_REVIEW" or category == "Outros":
    enqueue_for_review(merchant, suggestion, confidence)
    # NÃO persiste em memory
```

## Por que NÃO usar "sempre confirm before applying"

Foi tentado em iteração anterior. Resultado: ruído enorme. O usuário tinha que aprovar categorias óbvias (LIDL, MEO) toda vez. Cancelado.

## Por que NÃO usar "always apply AI silently"

Foi tentado em iteração anterior. Resultado: transações mal-categorizadas entravam sem revisão. O usuário perdeu autoridade sobre a primeira impressão. Cancelado.

## Permanecer no caminho atual

Primeiro encontro → review. Aprovação persiste em memory. Próximos encontros → auto. Não mude isso sem o usuário pedir.
