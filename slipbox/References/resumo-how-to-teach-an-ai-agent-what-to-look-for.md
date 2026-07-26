---
title: "How to Teach an AI Agent What to Look For (Without Prompting)"
source: https://www.asianefficiency.com/productivity/how-to-teach-ai-agent-without-prompting/
date: 2026-07-26
tags: [ia, automacao, agentes, devops, asian-efficiency]
---

# Como ensinar um agente de IA o que procurar (sem prompting)

Thanh Pham, da Asian Efficiency, inverte a intuição padrão sobre construção de agentes. A maioria das pessoas começa pelo prompt: senta, escreve o workflow desejado, conecta ferramentas. "Isso está ao contrário." O primeiro passo real é ensinar o agente a reconhecer o gatilho — e a forma mais rápida de fazer isso não é escrever, é **mostrar**. O artigo usa um caso concreto: automação de lembretes de pagamento da Payoneer para uma cliente CPA, Amanda. Antes de qualquer linha de lógica, Pham pediu uma screenshot do e-mail inteiro.

O problema de reconhecimento é o cerne técnico. Um agente não consegue identificar um tipo de e-mail só com descrição textual: "Quando receber um e-mail de lembrete de pagamento da Payoneer, adicione ao calendário." Não há como saber, a partir dessa frase, qual o formato do remetente, o padrão do assunto, a estrutura do corpo, o campo de valor. A screenshot vira **dado de treinamento** — não no sentido de fine-tuning, mas no sentido prático de "é isto que você está procurando no mundo real". O princípio generaliza: para qualquer agente que categorize, roteie ou redija, exemplos concretos batem descrições abstratas. Cinco recibos reais vencem uma definição de categorias de despesa.

A virada conceitual do artigo está na localização do trabalho difícil. A lógica "se X, então Y" é fácil. O trabalho pesado é o gatilho: descobrir como o agente identifica o momento de agir e tornar esse reconhecimento confiável o suficiente para disparar quando deve e não disparar quando não deve. No caso Amanda, depois da screenshot em mãos, o build no Lindy levou 15 minutos — todo o tempo real foi gasto no reconhecimento. Pham afirma que quase toda reclamação de "o agente não funciona" tem causa upstream: o gatilho não está sendo identificado corretamente. O método inicial proposto é documental — encontrar um exemplo real, capturar (screenshot ou arquivo), anotar o que se quer, e só então construir o workflow.

## Por que importa

- **Insight prático de engenharia de prompts/agentes**: contraria a tendência de gastar horas afinando texto de prompt. Para o perfil de quem trabalha com automação (Lindy, n8n, Zapier, scripts), essa inversão — **documentar com exemplos antes de promptar** — economiza tempo e reduz alucinação de gatilho.
- **Devops & reliability thinking**: a metáfora do "gatilho confiável" mapeia diretamente para o vocabulário de observabilidade e SRE — detectar o sinal certo, evitar falsos positivos. Mesma disciplina mental, aplicada a agentes em vez de serviços.
- **Cruzamento com teologia reformada**: a ideia de "a screenshot é o training data" lembra o princípio reformado de que a Palavra escrita é o exemplo concreto e suficiente que Deus nos dá — não um sistema de categorias abstratas. Show, don't describe: na revelação especial, Deus também escolheu mostrar antes de definir.

## Frases notáveis

> "The screenshot becomes the training data. Not in the deep-learning, model-training sense. In the 'here's exactly what you're looking for in the wild' sense."

> "When a client says 'the agent isn't working,' the problem is usually upstream of the workflow. It's not recognizing the trigger correctly."
