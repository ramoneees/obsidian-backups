---
title: "llm 0.37"
source: https://simonwillison.net/2026/Nov/2/llm/
date: 2026-11-03
tags: [ia, llm-cli, embeddings, open-source]
---

Simon Willison soltou a versão 0.37 do LLM, sua CLI e biblioteca Python para trabalhar com modelos de linguagem — dois meses de features acumuladas numa tacada só. Os destaques técnicos: novos modelos OpenAI (gpt-6.1-sol e gpt-6.1-terra), um comando llm openai endpoint add que simplifica configurar qualquer endpoint compatível com OpenAI, e o default agora é gpt-6-luna, metade do preço do anterior.

A mudança mais interessante para quem brinca com RAG: o suporte a embeddings agora aceita que conteúdos binários diferentes tenham content-types diferentes — necessário para modelos como o Gemini Embedding 2, que embute texto, áudio, imagem e vídeo. Ou seja: embedding multimodal virou cidadão de primeira classe na ferramenta, e busca semântica sobre mídia deixa de ser gambiarra.

Mas o parágrafo mais provocativo do post nem é sobre código. Willison, que recebe uma enxurrada de PRs assistidos por IA no projeto, diz que não vê isso como problema: ele usa Opus 5.5 ou GPT-6 Astra para triar as contribuições e trata cada PR como "um bug report com exemplo anexado" — às vezes aceita, às vezes escreve o fix ele mesmo. O release teve fixes de 12 autores, quase todos assistidos por IA, e o fardo de review foi menor do que ele esperava.

A tese implícita é incômoda para a Ortodoxia do Open Source: em vez de bloquear contribuições sintéticas, automatize a triagem e mude o contrato social do projeto. O maintainer deixa de ser gatekeeper de diffs e vira curador de hipóteses. Funciona quando você tem um LLM de ponta como filtro — o que levanta a questão de quem paga o cupom dessa triagem.

## Por que importa

- LLM é a peça central de qualquer pipeline de automação local — essa versão deixa configurar endpoints OpenAI-compatíveis (tipo o GLM que você já usa via zai) trivial: um comando, sem editar YAML na mão.
- Embeddings multimodais nativos abrem porta para busca semântica sobre áudio/imagem no teu vault e nos projetos (Casa da Cidade, faturas, sermões).
- O modelo de triagem de PRs assistida por IA é um playbook direto para precisase e tend: aceitar contribuição sintética como bug report, não como código final.

## Frases notáveis

> "I really see them as bug reports with attached examples - sometimes I land them, sometimes I implement my own fix."

> "A lot of open source maintainers complain about a flood of AI-assisted PRs. LLM is my project that has been most affected by this and, to be honest, I'm not finding it to be a problem."
