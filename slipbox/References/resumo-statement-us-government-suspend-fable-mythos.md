---
title: "Statement on the US government directive to suspend access to Fable 5 and Mythos 5"
source: https://simonwillison.net/2026/Jun/13/us-government-directive-to-suspend-access/
date: 2026-06-13
tags: [ia, anthropic, claude, regulacao, ai-safety, simon-willison]
---

# Statement on the US government directive to suspend access to Fable 5 and Mythos 5

Em 12 de junho de 2026, o governo dos EUA emitiu uma diretiva de controle de exportação obrigando a Anthropic a **suspender imediatamente o acesso a Claude Fable 5 e Mythos 5 para todos os clientes, incluindo funcionários estrangeiros da própria empresa**. A justificativa invocada é "segurança nacional": segundo o governo, surgiu um método de jailbreak para Fable 5. A Anthropic publicou uma nota pública deixando claro o seguinte: recebeu a diretiva às 17:21 ET do mesmo dia, sem detalhes técnicos específicos; revisou a demonstração e concluiu que a suposta vulnerabilidade é **amplamente disponível em outros modelos** (inclusive no GPT-5.5 da OpenAI), consistindo basicamente em pedir ao modelo para ler um codebase e encontrar falhas.

O ponto dramático é o precedente regulatório. O governo não exigiu recall de um produto com defeito material — exigiu o desligamento de um modelo *porque outro modelo equivalente já faz a mesma coisa*. O Simon Willison capturou a hora exata em que perdeu acesso via API: 18:59 PT (tentativa 37 bem-sucedida, tentativa 38 retornou 404 com a mensagem "Claude Fable 5 is not available"). A ação foi executada em ~3 horas entre a diretiva verbal e o corte. Willison aponta que, no momento da postagem, ele ainda conseguia acessar Fable 5 via claude.ai — ou seja, a fronteira entre "acesso por API" e "acesso por interface" virou o eixo de conformidade regulatória.

Há camadas aqui que valem destaque. Primeiro, o argumento da Anthropic desmonta a base técnica da diretiva: se outros modelos públicos têm a mesma capacidade, a medida não protege ninguém — só retira uma alternativa do mercado. Segundo, a *rapidez* e a *amplitude* (todos os clientes, globalmente) sugerem que a medida é política, não técnica. Terceiro, a instrução atinge funcionários estrangeiros da própria empresa, o que adiciona uma camada de soberania sobre mão-de-obra em IA que não tem precedente claro. É um capítulo inicial de como estados nacionais vão tentar controlar capacidades de fronteira de modelos, e o teste de fogo é: aceitar a lógica do "corte amplo" ou exigir que regulação de IA separe capacidade de modelo de produto comercializado.

## Por que importa

- Precedente direto sobre como regulação de IA pode ser usada como ferramenta de mercado disfarçada de segurança nacional.
- Para quem usa Claude via Hermes/OpenClaw, vale rastrear: a fronteira de acesso pode mudar por decreto, sem aviso e sem base técnica publicada.
- Cruzamento raro entre geopolítica, AI safety e arquitetura de produtos — tema que vai dominar o noticiário de IA nos próximos meses.

## Frases notáveis

- "The net effect of this order is that we must abruptly disable Fable 5 and Mythos 5 for all our customers to ensure compliance."
- "The level of capability displayed there is widely available from other models [...] and is used every day by the defenders who keep systems safe."
