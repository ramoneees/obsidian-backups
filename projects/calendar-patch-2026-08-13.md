# Calendar Patch — 10 itens faltantes detectados pelo Sprint Planning

**Gerado em:** 2026-08-13 20:53 (Sprint Planning Prep)
**Origem:** cruzamento Google Calendar (eventos das próximas 2 semanas) vs padrões do TickTick/Mind Sweep
**Status:** RASCUNHO — revise cada item, ajuste horários/datas conforme realidade, depois adicione manualmente no Calendar ou me peça pra criar via mcporter.

---

## Como aplicar

**Opção A (manual, recomendado pra revisar com calma):** abra Google Calendar e adicione cada item abaixo.

**Opção B (automático):** me diga "aplica todos" ou "aplica os X que eu marcar" e eu disparo via `mcporter call google_calendar create_event`.

---

## Itens a adicionar

### 1. Culto de Domingo (Igreja)
- **Quando:** todo domingo, horário a confirmar (provavelmente 10h ou 11h)
- **Duração:** ~1h30
- **Recorrência:** semanal, indefinida
- **Observação:** ⚠️ confirmar horário com a igreja antes de cravar. Se for só 1 horário (ex: 10h), criar como recorrente. Se houver 2 cultos, criar 2.

### 2. Pequeno Grupo (Igreja)
- **Quando:** sexta-feira, 20:00
- **Duração:** 3h (já está no Calendar em 14/08 e 28/08 — falta criar recorrência)
- **Recorrência:** quinzenal ou semanal? (veja no agendamento qual é o padrão)

### 3. Ensaio de Música
- **Quando:** se ainda é compromisso ativo, precisa de dia/horário fixo
- **Duração:** ~1h–1h30
- **Status:** ❓ você confirmou que ainda faz parte da rotina?

### 4. Natação Ramon
- **Quando:** a definir (separada da do Martim)
- **Duração:** ~45min–1h
- **Status:** ❓ você ainda nada? Se sim, que dias?

### 5. Reunião de Sprint Planning
- **Quando:** toda quarta-feira, 20:00
- **Duração:** 1h (gera o backlog automaticamente via cron job `6a46f1488896`)
- **Recorrência:** semanal, indefinida
- **Título sugerido:** "Sprint Planning Prep — revisar backlog gerado"
- **Status:** já existe como item de Mind Sweep, falta materializar no Calendar

### 6. Compras Mercado Semanal
- **Quando:** definir dia (sábado de manhã costuma ser comum)
- **Duração:** ~1h
- **Recorrência:** semanal
- **Observação:** atualmente é item solto, sem dia fixo

### 7. Bike 3x/semana
- **Quando:** 3 dias fixos a escolher (ex: seg/qua/sex ou ter/qui/sáb)
- **Duração:** ~45min–1h
- **Status:** ❓ você pratica atualmente? Se sim, marcar; se não, remover do Mind Sweep também

### 8. Rotina Diária Manhã (Ramonstro)
- **Quando:** todo dia útil, 07:45
- **Duração:** 30min (até 08:15)
- **Recorrência:** dias úteis (Seg–Sex)
- **Observação:** já aparece no Calendar de alguns dias mas falta criar recorrência oficial

### 9. Triagem Semanal Mind Sweep
- **Quando:** domingo de manhã (antes do culto, idealmente) ou segunda à noite
- **Duração:** 30min
- **Recorrência:** semanal
- **Observação:** evita o acúmulo que tá gerando ruído agora

### 10. Review Semanal (Semanal Review)
- **Quando:** domingo à noite
- **Duração:** 30min–1h
- **Recorrência:** semanal
- **Observação:** projeto 🗓 Semanal Review existe no TickTick mas sem tasks — ativar antes de marcar no Calendar

---

## Itens a remover/revisar

Estes não foram detectados como "faltando" mas merecem auditoria:

- **Pequeno Grupo quinzenal vs semanal** — ver se está marcado certo
- **Cinema em casa** (domingo 20:00) — recorrência semanal? Ou eventual?
- **Sermões excepcionais** (não recorrentes) — manter avulsos, ok

---

## Próximo passo

Me diga:
- **(a)** "Aplica todos" → eu crio via mcporter
- **(b)** "Aplica só 1, 2, 5, 8, 10" → curadoria mínima viável
- **(c)** "Não aplica agora, só guardo no Obsidian" → mantenho como referência

*Salvo em `~/obsidian-vault/projects/calendar-patch-2026-08-13.md`.*