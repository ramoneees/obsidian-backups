# Crédito Habitação BPI — Casa Própria (Plano 15 Anos)

> **Documento-mestre de longo prazo.** Indexado na memória vetorial (namespace `/memory/credito-habitacao`). Fonte: Carta Final + Minuta do contrato (gmail, operação 0120260037855-6572965, extraídos 2026-11-07). Plano operacional detalhado: `~/.hermes/plans/2026-11-07-credito-habitacao-15-anos.md`. Ledger: `Assets:Casa:Imovel` vs `Liabilities:PT:BPI:CreditoHabitacao`.

## Contrato (fatos verificados)

- Casa comprada em **06/10/2026 (escritura)**, habitação própria permanente, Caldas da Rainha.
- **Crédito a 100% do preço** via fiança do Estado (DL 44/2024, 15% do capital, 10 anos) — desembolso próprio = apenas impostos/custos de escritura (~€10,7k: IMT, selo, comissões, IRN).
- Mutuários: Ramon Carlos Pereira Rios + Renatha Laryssa dos Santos Oliveira.
- Montante: **€375.000,00** · Prazo: **420 meses (35 anos)** · Vencimento: prestações mensais.
- Taxa: **FIXA 36 meses @ TAN 3,413%** (Euribor 6M 2,713% + spread **0,700%**) → **VARIÁVEL 384 meses** (Euribor 6M + 0,700%), revisão pela média do mês anterior.
- Spread base **1,500%** (TAN 4,213%) se perder as condições comerciais (seguros/conta BPI) = **+€54,61/mês**. Seguros JÁ domiciliados: BPI Vida (€56,44/mês) + Allianz multi-riscos (DD BCP).
- Prestação atual: **€1.432,74** (com redução de 25bp). Stress máximo contratual: €2.272,93.
- **MTIC: €801.872,75** (custo total do crédito €426.872,75 — 2,14€ por euro emprestado).
- Juros de mora: TAN + 3%.

## Reembolso antecipado (a armadilha e a janela)

- **Durante os 36 meses de taxa fixa (até out/2029): comissão de 2%** (+ imposto de selo 4% sobre a comissão). Payback: 7 meses de juros — **NÃO amortizar antecipadamente neste período.**
- **Na fase variável (a partir de nov/2029): comissão de 0,5%** — payback 1,8 meses. **Amortizar aqui.**
- Parcial: só em data de prestação, aviso prévio de 7 dias úteis. Total: aviso de 10 dias úteis.
- Fim dos 36m fixos = **janela de renegociação** (novo período de taxa fixa + prazo podem ser recontratados nas condições comerciais vigentes — sem fee de amortização).

## A matemática (TAN 3,413% constante)

| Cenário | Prestação | Juros totais | Quitado em |
|---|---|---|---|
| Contrato (35a) | 1.432,74 | ~€268k (até €427k se Euribor subir) | out/2061 |
| 20 anos | ~1.912 | ~€143k | 2046 |
| **15 anos puro** | **~2.665** | **~€105k** | **out/2041** |

**Poupança 15a vs 35a ≈ €163.000.** Se a Euribor subir, a poupança CRESCE.

## O Programa 15 Anos (3 fases)

**Fase 1 — agora → out/2029 (meses 1–36, taxa fixa): NÃO amortizar.**
Pagar prestações normais. Construir o **Cofre de Amortização: €1.230/mês aplicados** (XP RendaFixa) → **~€44.280 em out/2029**. Mês 30–33: negociar com BPI a renovação da taxa fixa **com recontratação de prazo (~15 anos restantes)**.

**Fase 2 — nov/2029 (mês 37, fase variável): golpe único.**
Amortizar o cofre ~€44.280 (fee 0,5% ≈ €221). Saldo: ~€358k → **~€314k**. Se a rota da recontratação de prazo (Fase 1) tiver sido aceita, o BPI recalcula a prestação (~€2.660).
**⚠️ Na amortização parcial, pedir EXPRESSAMENTE "redução do prazo"** — por padrão o banco reduz a prestação mensal e mantém o prazo (o contrário do objetivo). A parcial deve coincidir com data de prestação (aviso 7 dias úteis).

**Fase 3 — nov/2029 → quitação: rampa conforme receita.**
| Extra/mês desde mês 37 | Casa quitada em |
|---|---|
| +€0 (só o cofre) | ~2047 |
| +€600 | ~2049 |
| +€900 | ~2046 |
| **+€1.230 (rampa 15a)** | **out/2041** |

Contexto de capacidade (nov/2026): fluxo de caixa ~zero; o contrato/receita nova financia a Fase 3. Cada +€300/mês encurta ~1,5 ano.

## Rastreio no ledger

- `Assets:Casa:Imovel` +375.000 vs `Liabilities:PT:BPI:CreditoHabitacao` −375.000 (patrimônio líquido neutro no dia 0).
- Cada prestação: split **juros** → `Expenses:Casa` (payee "JUROS DE EMPRESTIMO") / **capital** → reduz a Liabilities.
- Conta BPI da casa no Lunch Flow: lfid 45269 (`Assets:PT:BPI:Corrente`).
- Escola Martim (Colégio O Brinquinho, €324,66/mês) e condomínio saem da mesma conta → `Familia:Educacao` / `Casa`.
- **Pendente**: Plano de Reembolso oficial (BPI online → Documentos) para saldo devedor exato e split juros/capital preciso.

## Dívida unificada (novembro/2026)

| Dívida | Saldo | Juro | Estratégia |
|---|---|---|---|
| BPI Habitação | €375.000 | 3,413% fixa → E6M+0,7 | programa 15a acima |
| BCP Prestige | €4.022,65 | TAN 9,6% | fracionados no prazo; não girar percentual |
| Universo | €2.030,69 (acima do limite €2.000) | 18,5% fim-do-mês / 0% fracionada | NÃO usar o cartão; DD cobre fim-do-mês |
| Segurança Social (parcelado) | prestações ~€316 | — | manter parcelas (regularizado) |
| XP Visa / GO | ~R$250 / €0 | rotativo BR ~14%/mês se girar | GO: mudar opção 3%→100% |

## Marcos de decisão (calendário)

- **Dez/2026**: primeira prestação cheia (~€1.432,74) — confirmar split juros/capital no BPI.
- **Trim/2027**: revisar capacidade (contrato novo) → ajustar valor do cofre mensal.
- **Ago–out/2029 (meses 34–36)**: negociar renovação da taxa fixa + prazo com BPI. Decidir rota A (recontratar prazo) vs rota B (amortizar cofre + pagar 2.660/mês).
- **Nov/2029**: executar a amortização do cofre (fee 0,5%).
- **Anual (todo novembro)**: revisar este plano contra a realidade (Euribor, receita, saldo).
