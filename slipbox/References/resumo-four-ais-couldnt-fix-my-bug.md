---
title: "Four AIs Couldn't Fix My Bug. The Fifth One Did It in Minutes."
source: https://www.asianefficiency.com/technology/four-ais-couldnt-fix-it/
date: 2026-07-03
tags: [ia, llm, devops, multi-modelo, debugging, produtividade]
---

# Four AIs Couldn't Fix My Bug. The Fifth One Did It in Minutes.

Thanh Pham vinha construindo um assistente executivo de IA que conecta Slack, Telegram, Gmail e Google Calendar. A lógica de roteamento por intenção começou a falhar de maneira intermitente e difícil de isolar. Tentou Claude Code, depois o3, depois Gemini 2.5 Pro, depois Grok 3 — quatro modelos, quatro análises diferentes, quatro correções que não corrigiram. Duas horas investidas, bug de pé.

Instintivamente, pagou os US$ 30 do upgrade para o **Grok 4**. O modelo leu o código e devolveu algo qualitativamente diferente: em vez de patchear o sintoma, rastreou o fluxo lógico até a **origem real** — uma incompatibilidade na forma como a classificação de intenção era passada entre dois componentes. Root cause, não fix de superfície. Resolvido em minutos.

A leitura que Pham faz: os modelos têm **fortes diferentes**, ênfases de treino diferentes, abordagens diferentes. Claude Code é excelente para código de propósito geral e segurar muito contexto. Grok 4 (na experiência dele) tem força particular para rastrear fluxo lógico e achar causas raiz. São habilidades distintas. O problema da "lealdade de ferramenta" é que, quando um modelo falha, você assume que o problema é insolúvel. Muitas vezes o problema é só que **aquela ferramenta não é a melhor para aquele tipo específico de problema**.

Daí nasce o conceito de "multi-tool native": ChatGPT para estratégia e pesquisa, Claude para raciocínio técnico e código, Gemini para tarefas visuais e workflows Google-native, Grok para dados em tempo real e debugging de causa raiz, Perplexity quando precisa de informação sourced e atual. A prática operacional virou a regra dos "Três Cérebros": quando algo empaca, descreva o problema simultaneamente para vários modelos, ache onde concordam e onde divergem, combine o mais crível, devolva ao modelo de execução. Minutos extras no início para evitar horas de loop.

A conta final: US$ 30 de upgrade vs. 2 horas já gastas. A matemática de tentar ferramentas diferentes é quase sempre favorável. O gargalo não é preço — é a **suposição de que se um modelo não conseguiu, nenhum consegue**. Pham reescreve o aprendizado de carreira: a habilidade com IA não é encontrar a melhor ferramenta e dominá-la. É **roteamento** — saber qual especialista trazer para qual trabalho, e estar disposto a trocar quando o primeiro não resolve. Lealdade a ferramenta é passivo. Letramento de ferramenta é a skill.

## Por que importa

- Dá **evidência anedótica forte** contra a mentalidade de "achou o melhor modelo, acabou a busca" — útil para o próprio workflow de Ramon com múltiplos modelos no Hermes/Claude Code/o3.
- O framework "Três Cérebros" é diretamente aplicável a debugging de infraestrutura e código na rotina devops: roda o mesmo problema em paralelo, extrai consenso, executa no modelo de produção.
- Introduz o conceito de **multi-tool native** como skill do momento — contraponto direto ao culto de persona única de IA que domina o mercado.

## Frases notáveis

> "Tool loyalty is a liability. Tool literacy is the skill."

> "Asking one model to do everything is like hiring a copywriter and expecting them to also debug your database. They might try. They won't do it as well as someone for whom that's a core skill."
