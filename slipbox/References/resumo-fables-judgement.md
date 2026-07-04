---
title: "Fable's judgement"
source: https://simonwillison.net/2026/Jul/3/judgement/
date: 2026-07-04
tags: [ia, prompt-engineering, claude-code, coding-agents, automacao]
---

## Resumo

Simon Willison destila uma dica prática vinda do time do Claude Code: em vez de ditar regras granulares ("rode testes só em features grandes, pule em mudanças de copy"), deixe o próprio modelo decidir. O exemplo canônico é dizer "use seu próprio judgement para decidir quando escrever testes" — abrindo mão do controle fino em troca da autonomia do agente.

O autor aplica o princípio ao problema mais urgente que tem agora: Fable é caro e seu allowance de uso está acabando antes da janela de preços mudar. Em vez de mapear manualmente qual modelo serve para qual tarefa, ele adiciona uma instrução persistente na memória do projeto Claude Code: "para tarefas de coding, use seu judgement para escolher um modelo mais barato via subagent". Sonnet para implementação substantiva, Haiku para edições triviais. Design, auditoria e síntese continuam no modelo principal.

O Claude Code salvou isso como um memory file estruturado em YAML, com nome, descrição, metadata de tipo (feedback) e a sessão de origem. Willison reporta que está funcionando bem: muito trabalho entregue com o allowance de Fable diminuindo mais devagar. O insight de fundo é que "judgement" virou uma primitiva delegável — a melhor forma de gastar tokens de topo de linha é justamente pedindo que o modelo decida quando não os gastar.

## Por que importa

- Para o workflow devops/automação do Ramon: o padrão "delegue ao judgement do modelo, não prescreva o caminho" é uma inversão de mentalidade aplicável diretamente a pipelines com agentes — em vez de hardcodar qual LLM faz o quê, deixe o orquestrador rotear.
- Cruza com teologia reformada de forma provocativa: delegar julgamento é um ato de confiança calibrada. Funciona em IA porque o modelo tem competência; a pergunta análoga em liderança eclesiástica é quando confiar no critério de outro sem sufocar.
- O memory file em YAML é um padrão reutilizável para qualquer setup de Claude Code — vale copiar a estrutura para o vault.

## Frases notáveis

> "Tell Fable to use other models for smaller tasks, applying its own judgement about which model to use."

> "judgement, review, and synthesis stay with the main loop."
