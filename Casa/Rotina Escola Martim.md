# Rotina Escola Martim — Colégio O Brinquinho

> **Princípio: zero decisão de manhã.** Decisão em lote (domingo), execução em sequência fixa (todo dia igual).
> Entrada **9:00** · Saída de casa **8:45** · Seg–sex

## As 3 camadas

### 1. Caixa da Semana — domingo 20:00, 15 min
Organizador com 5 divisões etiquetadas **SEG–SEX** (pendurar ou empilhar perto de onde ele se veste).

- [ ] Ver previsão do tempo da semana
- [ ] Separar 5 kits completos (corpo, meias, underwear, calçado se aplicável)
- [ ] Confirmar **kit reserva** na mochila: 1 muda completa em saco plástico
- [ ] Confirmar **cardigã universal** no gancho fixo perto da porta

### 2. Noite anterior — 5 min, junto do banho/jantar
- [ ] Mochila pronta (água, lanche, fichas/avisos da escola)
- [ ] Kit do dia em cima da cômoda / divisão da caixa apontada

*Regra: a noite resolve o que a manhã não deve decidir.*

### 3. Manhã — sequência fixa, sempre a mesma ordem
Checklist **visual** (figuras) colado na altura do Martim:

**acordar → xixi → vestir (kit do dia) → café → dentes → sapatos → sair**

| Hora | Âncora |
|------|--------|
| 8:35 | Alerta no telemóvel (10 min: sapatos/jaqueta, sair) |
| 8:45 | Sair de casa |
| 9:00 | Entrada no colégio |

Ele executa figura melhor do que comando — autonomia dele, menos direção dos pais.

## Fallbacks (a rotina não quebra por exceção)
- **Frio inesperado** → cardigã do gancho. Não reabrir a caixa.
- **Roupa suja/acidente** → kit reserva da mochila; repor à noite.
- **Kit faltando na divisão** → puxar de outra divisão; anotar repor sexta.
- **Sexta à noite** → conferir estoque de roupa limpa + encher saco de lavar (a lavanderia tem que rodar ANTES do domingo).

## Ganchos no sistema (já criados)
- Dom 19:30 — briefing no iMessage: kits por dia + pijamas + o que puxar (script `~/.hermes/scripts/kits_martim.py`, cron `d66a0c7188af`). Zero decisão: só executar a mensagem.
- Dom 20:00 — "Montar kits da semana — Martim" (Home, alerta na hora)
- Seg–sex 8:45 — "Saída — Escola Martim" (Home, alerta 8:35)
- Inventário de roupas: `Casa/Roupa Martim.md` — contar na sexta ao dobrar (5 min); abaixo do mínimo → repor

## Manutenção
- Férias/feriados: pedir ao Jarvis para suspender/restaurar as séries.
- Ajustar horário de saída: uma linha de comando, avisar o Jarvis.
