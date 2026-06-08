# Crisp — Bot Commands Reference

Documento vivo. Atualizado quando um comando novo entra ou sai.

## Telegram: @CrispRamoneeesBot

### Comandos registrados (BotFather)

| Comando | Descrição | O que faz |
|---|---|---|
| `/start` | Saudação inicial | Responde com identidade Crisp + atalho pra `/help` |
| `/help` | Lista de comandos | Mostra tabela completa |
| `/status` | Saúde do agente | Model, última atividade, próximo deadline, sessões ativas |
| `/saldo` | Saldo das contas | Lista contas Firefly-III com saldo atual |
| `/faturas` | Faturas pendentes | Lista Invoice Ninja pendentes, ordenado por vencimento |
| `/despesas` | Despesas do mês | Soma por categoria, comparação com mês anterior |
| `/briefing` | Sumário do dia | Saldo + faturas próximas + deadline fiscal + fluxo recente |

### Comandos reservados (futuro)

| Comando | Status | Planejado |
|---|---|---|
| `/fechar-mes` | 🔜 | Checklist de fechamento mensal |
| `/fechar-trimestre` | 🔜 | Checklist de fechamento trimestral (IVA) |
| `/backlog` | 🔜 | Lista de coisas pendentes detectadas |
| `/pagar [id] [método]` | 🔜 | Marca fatura paga em Invoice Ninja + cria transação Firefly |
| `/exportar` | 🔜 | Exporta dossier do mês pro contabilista |
| `/ajuda` | alias de `/help` | Idem |

### Comandos escondidos (over 30 limit)

O gateway descobre ~106 comandos adicionais automaticamente, vindos das skills carregadas. `/commands` no Telegram mostra a lista completa. A maioria são atalhos pra fluxos internos (rollback, /sessions, /config) que você não precisa usar.

## CLI: `crisp chat`

Para sessões locais longas (Telegram tem limite de tamanho de mensagem).

```bash
crisp chat                              # interativo
crisp chat -q "saldo das contas"        # one-shot
cresp -p crisp -c                       # continua última sessão
```

## Aliases do shell (recomendado adicionar)

```bash
# ~/.bashrc ou ~/.zshrc
alias c='crisp chat -q'                 # atalho one-shot
alias cc='crisp chat'                   # interativo
```

## Filtros avançados (futuro)

```
/faturas atrasadas       # só vencidas
/faturas semana          # vence em 7 dias
/despesas categoria X    # filtra por categoria
/saldo conta NOME        # só uma conta
```

---

**Última atualização:** Jun 2026
**Mantido por:** Crisp (perfil Hermes) + Ramon (revisão)
