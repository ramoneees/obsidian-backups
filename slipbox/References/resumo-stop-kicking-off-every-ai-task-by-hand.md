---
title: "Stop Kicking Off Every AI Task by Hand"
source: https://www.asianefficiency.com/technology/stop-kicking-off-ai-tasks/
date: 2026-09-20
tags: [automacao, ia-agentes, workflows, produtividade]
---

A tese é provocativa na simplicidade: se você inicia cada tarefa de IA à mão ("escreve esse slide", "gera essa imagem"), você é o gargalo. O artigo chama isso de *kickoff vibe* — ok para aprender, péssimo como regime permanente. A alternativa é a "Software Factory": construir rotinas, skills e contexto para que a IA execute continuamente, sem você disparar cada job. Seu papel muda de operador para afinador.

O mapa tem cinco camadas: Capture, Triage, Planning, Execution, Review. A regra é não automatizar as cinco de uma vez — identificar a camada com mais atrito e começar por ela. Capture costuma ter o maior ROI: se a IA não vê o e-mail, o Slack e as transcrições de reunião, Planning e Execution são chute. A promessa perdida do "te respondo depois" enterrado no chat diário é sintoma clássico de Capture quebrado.

Nas camadas intermediárias, o critério de decisão é honesto: IA para triagem de arquivos é *good-enough accuracy* — se um documento mal arquivado dói de verdade, use código determinístico. Na execução, ensinar sua voz exige editar **com** a IA (4–5 rodadas de feedback até os rascunhos chegarem com seu tom) e dar a cada projeto um `Taste.md` com preferências de design e regras de tom — a IA auto-checa antes de entregar, e você corta os loops repetitivos de feedback.

O pulo do gato está no Review, exemplificado pelo erro "June vs. July" de um post backdated: quando a IA erra, não corrija só o output — atualize o skill/prompt para que aquela **classe** de erro seja pega na próxima vez. É Kaizen aplicado a agentes: uma melhoria sistêmica por semana, em vez de uma lista mental de "lembrar de conferir a data".

## Por que importa
- É a arquitetura que você já vive na prática (Hermes, crons, agentes em worktrees) — as "5 camadas" dão vocabulário para auditar onde ainda há kickoff manual escondido.
- "Erro → atualizar o sistema, não só o output" é o mesmo padrão confrontar→plano→executar; vale para skills do Hermes e prompts de agente.
- Linha de decisão nítida: bom-o-suficiente para IA, determinístico quando precisão importa — quando usar agente e quando usar código.

## Frases notáveis
> "Stop manually kicking off individual AI tasks… Build the machine instead: routines, skills, and context."

> "Your role shifts from writer to tuner."
