# Finances — Master Index

Workspace de gestão financeira, mantido por Crisp (perfil Hermes dedicado).

## Estrutura

```
finances/
├── INDEX.md              ← você está aqui
├── BOT_COMMANDS.md       ← comandos disponíveis no Telegram/CLI
├── snapshots/            ← saldos mensais (auto-gerado)
├── dossiers/             ← 1 por tema: trimestre IVA, ano fiscal, etc
├── clients/              ← 1 dossier por cliente (4Mation, Flexiana, ...)
└── templates/            ← templates reutilizáveis (reconciliação, briefing, ...)
```

## Estado atual (Jun 2026)

| Sistema | Status | Detalhe |
|---|---|---|
| **Firefly-III** | ⚠️ Token expirado | Precisa gerar novo Personal Access Token |
| **Invoice Ninja** | ✅ Online | `Ramon Carlos & Renatha LDA`, 2 clientes, 6 invoices |
| **Obsidian** | ✅ Estrutura criada | Esta pasta |
| **Octa Manager** | 🔜 Não integrado | Conforme mencionado na memória, Ramon integra manualmente |

## Pendências (Jun 2026)

- [ ] Regenerar token Firefly-III (acesso via web UI > Options > Profile > Personal Access Tokens)
- [ ] Configurar cron de briefing diário (após Firefly voltar)
- [ ] Primeira invoice testada com classificador (C4)
- [ ] Test plan gemma4 vs MiniMax-M2.7 (C5)

## Como usar

**Caminho rápido (sem perguntar pro Crisp):**
- Saldo? → consulta `snapshots/YYYY-MM-accounts.md`
- Faturas pendentes? → consulta `clients/4Mation.md` ou `clients/Flexiana.md`
- Dúvida fiscal? → abre `dossiers/<trimestre>.md` ou consulta skill `crisp-portuguese-tax-calendar`

**Caminho com Crisp (recomendado):**
- Telegram: `@CrispRamoneeesBot`
- CLI: `crisp chat` ou `crisp chat -q "pergunta"`
- Skill de onboarding: `crisp-onboarding` (cobre setup inicial completo)

## Convenções

- **Datas:** ISO `YYYY-MM-DD` em todos os ficheiros
- **Valores:** sempre em EUR, duas casas decimais
- **Naming:** tudo o que vai pra contabilista segue `MM_YYYY_TIPO_Emitente.pdf` (ver memória do Crisp)
- **Frequência de snapshot:** mensal, no primeiro dia útil

---

**Mantido por:** Crisp + Ramon
**Última atualização:** Jun 2026
