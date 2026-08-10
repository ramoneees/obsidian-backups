---
title: "Auto mode is now the default in Claude Code for Pro, Max, and Team plans"
source: https://simonwillison.net/2026/Aug/8/auto-mode/
date: 2026-08-10
tags: [ia, devops, claude-code, seguranca, prompt-injection]
---

# Auto mode é o novo padrão no Claude Code

**Anthropic anunciou em 08/08/2026** que o *auto mode* do Claude Code — onde o agente decide sozinho se cada ação precisa de aprovação humana — virou default em Pro, Max e Team plans a partir de 14/08. **Simon Willison** comenta o movimento e o número que justifica a confiança da Anthropic: em teste com 1.053 devs pagos, **89% das ações perigosas foram bloqueadas pelo auto mode contra apenas 13,6% dos humanos** que revisaram prompts trocados por comandos hostis no meio da sessão.

A Anthropic também publicou evals da Trajectory Labs: **0 de 720 ataques de prompt injection indireto passaram** contra Claude Fable 5, Opus 5 e Sonnet 5 rodando em auto mode. Thariq Shihipar tuitou que deveriam ter chamado o post de *"defeating the lethal trifecta"*.

Willison, no entanto, **segue cético e o diz explicitamente**. Sua crítica principal: a Anthropic está provando que *humanos são ruins* de revisar — mas isso é faca de dois gumes. Significa que estamos terceirizando decisões de segurança irreversíveis (deletar produção, exfiltrar dados) para um classificador, e os 11% que o auto mode *não* pega, ou o pacote malicioso de terceiro que ele não consegue detectar, vão causar danos sem aviso. Ele reforça a previsão de janeiro: 2026 terá um *"challenger disaster"* em segurança de coding agents.

A pergunta de fundo: **você prefere um humano cansado clicando OK a cada 3 segundos, ou um modelo que erra 11% das vezes sem ninguém assistindo?** A Anthropic apostou que a segunda opção é, na média, mais segura. Willison concorda em média — mas não nos piores casos.

## Por que importa

- **Decisão arquitetural para qualquer dev que roda agentes**: se você usa Claude Code, Codex CLI ou similares, o auto mode redefine o contrato de execução. Vale repensar o que cada agente tem acesso (tokens, credenciais, branches de produção) — o modelo agora decide sozinho.
- **Caso de estudo sobre "confirmation fatigue"**: o dado de 13,6% vs. 89% é uma refutação empírica do "human-in-the-loop" como controle de segurança. Tem implicação direta para qualquer sistema de aprovação humana (CI gates, code review, moderação de conteúdo).
- **Provocação epistemológica**: o que significa "mitigar todo ataque" quando o atacante é criativo e o classificador é estático? É o mesmo problema de teologia da providência vs. liberdade — só que com LLMs.

## Frases notáveis

> "Of course, that still leaves 11% of cases where auto mode would *not* have prevented the action!"

> "I'm on the record predicting 'a challenger disaster for coding agents security' for 2026. I would dearly like to be proved wrong by the end of this year."
