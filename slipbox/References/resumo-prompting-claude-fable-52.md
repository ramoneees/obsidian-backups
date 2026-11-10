---
title: "Prompting Claude Fable 5.2"
source: "https://simonwillison.net/2026/Nov/10/prompting-claude-fable-52/"
date: 2026-11-10
tags: [prompt-engineering, ai, agentes, llms]
---

Willison destaca um achado da documentação oficial de prompting do Claude Fable 5.2: o modelo responde fortemente à moldura de "quem é o dono do código". Nos testes da Anthropic, quando o prompt não dizia nada sobre ownership — ou apresentava o codebase como coisa de outra pessoa — o modelo tendia a apenas acrescentar em cima da estrutura existente, mesmo quando isso significava duplicar código que já estava lá.

A correção custa uma frase. Declarar "este codebase é seu: o que ele faz e como é construído é decisão sua, e você vai continuar construindo nele" fez o modelo fundir código repetido em cerca de metade das tentativas — contra menos de um décimo sem a frase. Mesma tarefa, mesmo modelo; só mudou a narrativa de posse, e o comportamento estrutural mudou junto: de acumulador para mantenedor.

É engenharia de prompt no nível certo: não microinstrução de tarefa, mas definição de relacionamento. Vale tratar como knob padrão em qualquer prompt de manutenção de longo prazo — e com a ressalva honesta de que os testes foram em tarefas pequenas, então é heurística forte, não garantia.

## Por que importa

- Aplicável hoje: uma linha nos prompts dos agentes do Ramon (OpenCode, Sisyphus, revisões do Claude Code) pode virar o comportamento de "empilhar" para "refatorar".
- Conecta com o workflow dele de code review pós-agentes — o tipo de dívida técnica (código duplicado, estrutura ignorada) que ele caça manualmente pode ser prevenida no prompt.
- Material para o cruzamento teologia × tecnologia: posse como moldura comportamental abre conversa sobre stewardship — agentes (e pessoas) cuidam melhor do que lhes é confiado como próprio.

## Frases notáveis

> "This codebase is yours: what it's for and how it's built are your call, and you'll keep building on it."

> "The model merged repeated code in about half of the tries with this sentence, and in under a tenth of the tries without it."
