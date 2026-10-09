---
title: "Yes, and... (Carson Gross sobre IA e o futuro da programação)"
source: https://htmx.org/essays/yes-and/
date: 2026-10-09
tags: [ia, programacao, carreira, llm]
---

Carson Gross — criador do htmx e professor de ciência da computação — responde à pergunta "dado a IA, ainda vale virar programador?" com "Sim, e...". O "sim": programação é, no fundo, resolução de problemas com computadores + controle de complexidade, e ele não consegue imaginar um futuro onde isso valha menos que hoje. O "e": o que muda é a mistura de habilidades — comunicação clara, entendimento de negócio e arquitetura de sistemas ganham valor relativo enquanto o código bruto perde.

A parte provocativa é o alerta aos juniores: IA é perigosa para quem está começando justamente porque gera código eficaz. Quem nunca escreveu código não aprende a LER código — e ler será ainda mais valioso num futuro de código gerado. Quem não lê cai na Armadilha do Aprendiz de Feiticeiro: sistemas que não entende e não controla. Gross também desmonta a analogia "montagem → linguagem de alto nível": compiladores são determinísticos, LLMs não — código gerado por LLM frequentemente ADICIONA complexidade acidental em vez de eliminá-la. Se você não sabe ler código, como perceber isso?

Para seniors, o perfeito é outro: parar de programar e entrar em "brain rot", rolando prompts eternamente enquanto espera. Sua lista pessoal de uso saudável de LLMs: analisar código existente, organizar pensamentos, gerar pedaços pequenos, escrever o que ele odeia escrever (regex, CSS), protótipos descartáveis e sugerir testes. E uma linha que deveria estar emoldurada: "Eu nunca deixo LLMs projetarem as APIs dos sistemas que construo."

Ele ainda distribui um AGENTS.md aos alunos para configurar agentes como um ótimo monitor (TA) em vez de gerador de código — e termina com conselho de carreira: vagas online são loteria; as quatro famílias (Family, Friends, Family of Friends) são o caminho, porque toda empresa com mais de 100 pessoas tem problemas para resolver com código.

## Por que importa

- Contraponto direto ao workflow do Ramon: delegar coding a agentes é legítimo, mas "nunca deixar LLM desenhar APIs" bate exatamente na zona onde mora o port-driven design — julgamento arquitetural permanece humano.
- A tese central (ler código > escrever código) valida a stack de orquestração: plan → review → exec, onde a skill crítica do orquestrador é avaliar, não digitar.
- O AGENTS.md como "TA configurado" é um padrão roubável para os agentes do Ramon: menos gerador, mais parceiro de entendimento.

## Frases notáveis

> "Yes, AI can generate the code for this assignment. Don't let it. You have to write the code."

> "If you can't read the code you are going to fall into The Sorcerer's Apprentice Trap, creating systems you don't understand and can't control."
