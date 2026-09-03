---
title: "llm-gemini 0.34"
source: "https://simonwillison.net/2026/Sep/2/llm-gemini/"
date: 2026-09-03
tags: [ia, llm, gemini, devops]
---

# llm-gemini 0.34

**Simon Willison · simonwillison.net**

## Resumo

Release note curta, mas com payload: o plugin `llm-gemini` do ecossistema LLM de Simon Willison chegou à versão 0.34 com suporte ao recém-lançado **Gemini 3.8 Flash** — com os três níveis de thinking (low/medium/high). O Google também lançou um 3.8 Flash Cyber, mas restrito a "trusted defenders". Correção de bug: responses assíncronas agora registram corretamente a versão resolvida do modelo.

Willison faz o seu ritual de benchmark estético — o pelicano de bicicleta em SVG nos três níveis de thinking — e depois mostra o que importa na prática: pediu "make me a cool thing in html" e o modelo entregou um demo funcional em 13 segundos, custo de 1,8 centavos de dólar. A avaliação dele em uma frase: Gemini Flash é "rápido, barato e competente em coisas como HTML e JavaScript".

O detalhe mais interessante para quem constrói: ele usou o próprio 3.8 Flash com o plugin `llm-coding-agent` para estender sua ferramenta `markdown-svg-renderer` e adicionar renderização de HTML em iframe sandboxed — ou seja, o modelo de baixo custo já é competente o bastante para fazer maintenance real de ferramentas de código, com transcript público no gist.

O padrão da cultura dev que o blog encarna: release note de 5 linhas vira demonstração de workflow completo — modelo novo → teste de qualidade visual → tarefa real de engenharia → artefato publicado com transcript. Rastreabilidade como hábito, não como exigência.

## Por que importa

- **Gemini 3.8 Flash direto no CLI** — para o stack pessoal (roteamento pesado→GLM, privado→Qwen), um modelo rápido/barato/competente em código HTML+JS é candidato natural a tarefas utilitárias e agentes de baixo custo via `llm`.
- **Custo-benefício mudando de escala** — demo funcional em 13s por 1,8¢ sinaliza que a barra do "bom o suficiente para manutenção de ferramentas" já foi cruzada pelos modelos flash; afeta a arquitetura de agentes (quando delegar pro modelo barato).
- **Transcript público como cultura** — publicar o transcript do agente junto com o artefato é exatamente o tipo de rastreabilidade que separa automação séria de protótipo frágil.

## Frases notáveis

> "Something I appreciate about Gemini Flash is that it's fast, cheap, and competent at things like HTML and JavaScript."

> "I prompted 'make me a cool thing in html' and it built this... Took 13 seconds, cost 1.8 cents."
