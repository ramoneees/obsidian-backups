---
title: "Let the AI Show You the Plan Before It Touches a File"
source: https://www.asianefficiency.com/technology/ai-show-plan-before-file/
date: 2026-11-16
tags: [automacao, agentes, produtividade]
---

Thanh Pham descreve seu fluxo de automação com agentes: durante uma caminhada de 45 minutos, ditou por voz a criação de um deck de slides e dos arquivos de demonstração; a revisão ficou para uma sessão separada. O princípio central: você especifica o resultado em inglês simples e confere o trabalho — o código fica por conta do setup.

O coração do método é o loop PAVE: **P**oint (aponte para a pasta/tarefa), **A**sk (pergunta como a IA trataria), **V**erify (verifica o plano proposto você mesmo), **E**xecute (só executa após aprovação — e confere de novo o resultado). Em pastas, o primeiro pedido é sempre um inventário somente-leitura: nome atual, conteúdo, categoria proposta, nome sugerido, nível de confiança. Só depois de ler a tabela é que se autoriza renomeações.

Ele propõe quatro perguntas antes de automatizar qualquer coisa: a IA acessa os inputs? Você sabe descrever um bom resultado em linguagem plana? Dá para verificar o trabalho em menos de dois minutos? Um erro seria fácil de reverter? Se a tarefa não passa nas quatro, escolha outra menor — e teste sempre numa cópia com arquivos descartáveis primeiro.

Quando a limpeza vira rotina agendada, ele recomenda começar no menor dos três níveis de autonomia: report first. A IA reporta e pede aprovação; só depois de aprender o que o sistema faz é que se libera "age on confident cases, flag the rest" e, por fim, autonomia total. E uma regra de ouro para pastas compartilhadas: dois agentes podem inspecionar, mas só um escreve por vez.

## Por que importa

- É literalmente o workflow do Ramon (confrontar → plano → executar) publicado por outra pessoa — o PAVE é a mesma disciplina com outro nome, incluindo o inventário read-only antes de qualquer PATCH.
- Os quatro filtros (acesso, resultado describível, verificação < 2 min, erro reversível) são uma régua prática para decidir o que automatizar na casa e no precisase sem virar firewall de micro-aprovações.
- "Report first" e "um escritor por pasta" mapeiam direto para o kanban tekton e para worktrees separadas: agentes paralelos podem ler juntos, mas merge/escrita é serializada.

## Frases notáveis

> "You are specifying the result and checking the work."

> "Beginners should report first, so you can learn what the system does before you give it more freedom."
