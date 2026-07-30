---
title: "AI Worming through Word"
source: https://simonwillison.net/2026/Jul/29/ai-worming-through-word/
date: 2026-07-30
tags: [ia, seguranca, prompt-injection, devops]
author: Simon Willison
---

## Resumo

Link-post do Simon Willison comentando pesquisa de Håkon Måløy sobre uma nova variante de ataque de prompt injection que se replica sozinha. O vetor é o Microsoft Copilot para Word: um atacante insere instruções ocultas (texto branco sobre branco, por exemplo) em um documento. Quando esse documento é usado como material-fonte pelo Copilot, o agente interpreta as instruções ocultas como parte do pedido do usuário e manipula o documento em edição — em seguida, copia as próprias instruções para o documento resultante, transformando-o em novo portador.

O efeito é o de um worm auto-replicante: cada documento gerado pelo Copilot infectado carrega a carga útil adiante. Se esse novo documento entrar em outro workflow assistido por Copilot, o ciclo se repete — sem que o documento original do atacante precise estar presente. É a primeira vez que Willison vê um exemplo de hidden instructions que deliberadamente se copiam para se auto-replicar.

A disclosure foi responsável à Microsoft, que teve 144 dias para trabalhar em mitigação. Até a publicação, não havia correção que cobrisse a classe inteira do ataque — o que Willison classifica como "unsurprising" dado que se trata de uma propriedade estrutural de LLMs que seguem instruções do contexto.

## Por que importa

- **Segurança de IA corporativa**: qualquer workflow de devops que integre Copilot, Claude ou ChatGPT em pipelines com documentos (Word, Notion, PDFs) precisa reconsiderar o modelo de ameaça. Tratar documentos como "dados" e não como "código executável" deixou de ser seguro.
- **Ataque sistêmico, não pontual**: o aspecto worm-like muda a análise. Não basta filtrar inputs conhecidos — é preciso assumir que qualquer contexto pode conter instruções hostis e usar arquiteturas que separem dados de instruções (ex.: tagging de proveniência, sandboxes instrucionais).
- **Cruzamento técnico-filosófico**: a falha não é bug, é feature — LLMs são otimizados para seguir instruções. Há aqui um problema análogo à tensão entre controle e escuta discutida na tradição reformada: sistemas criados para "responder" ao mundo podem silenciar a distinção entre sinal e ruído.

## Frases notáveis

> "Copilot may then also copy the hidden instructions into the resulting document, turning that document into a new carrier."

> "It was responsibly disclosed to Microsoft who then had 144 days to work on a fix, but so far (unsurprisingly) there's no mitigation that covers the full class of attack."
