---
title: "There are no lossless transformations of natural-language text"
source: https://simonwillison.net/2026/Aug/11/there-are-no-lossless-transformations-of-natural-language-text/
date: 2026-08-12
tags: [ia, llm, escrita, produtividade, etica-ia, simon-willison]
author: Sophie Alpert (com curadoria de Simon Willison)
---

# There are no lossless transformations of natural-language text

## Resumo

Sophie Alpert, engenheira-chefe da Clay, escreveu uma política interna sobre uso aceitável de IA em redação técnica e a publicou — texto curto que sustenta a própria tese. Willison faz a curadoria porque, segundo ele, a formulação de Sophie captura algo que a comunidade de LLM vinha evitando dizer em voz alta. A premissa central é simples e brutal: **não existe transformação sem perda de linguagem natural**. Cada reescrita, cada "polishing" via Claude, cada parágrafo "melhorado" pelo GPT altera o significado — e quando a entidade que reescreve não carrega sua representação mental detalhada, informação se perde.

A regra de ouro que Sophie extrai disso: **você precisa endossar cada ideia e cada frase**. Se um colega pergunta "o que você quis dizer aqui?", não é aceitável responder "ah, foi a IA, ignora". Isso confunde leitores, desperdiça o tempo deles e, pior, substitui a *sua* voz por uma voz estatisticamente plausível. A política explicita: é permitido usar IA para brainstorming, redação inicial e proofreading — mas todo o conteúdo precisa permanecer representativo do seu pensamento real.

O argumento mais provocativo é epistemológico: **"writing is thinking"**. Documentos como specs, status reports e incident retros não são entregáveis burocráticos; são *prova de pensamento*. O artefato não é o objetivo — o pensamento detalhado sobre o problema é o objetivo. Subcontratar a escrita à IA para pular esse processo é subverter a própria função do documento. Se você precisou escrever, era porque precisava pensar. Willison, no link post, sublinha o ponto: longa ≠ melhor. Pascal escreveu que fez a carta mais longa que o habitual por não ter tempo de fazê-la mais curta. IA torna a geração preguiçosa de texto longo trivial — e uma de suas estratégias é encher páginas de frases vazias que diluem o conteúdo real.

O fechamento é metodológico: como a IA ainda não tem teoria da mente razoável nem consegue replicar a representação mental do autor, princípios éticos de escrita permanecem até quando a ferramenta melhorar. A IA pode polir; não pode pensar por você. Sophie libera, contudo, um uso: citar verbatim uma geração IA, *desde que claramente marcada como tal* ("o Claude sugeriu isso, vale investigar?"). É uma saída honesta para o trabalho exploratório que se beneficia do espaço latente do modelo.

## Por que importa

- É a crítica mais clara e operacional disponível contra a tendência de "vibe writing" — usar LLM para gerar documentos que parecem competentes mas dizem pouco. Conecta-se diretamente ao trabalho de Ramon com automação e produção via IA.
- A máxima "writing is thinking" tem ressonância teológica: a tradição reformada sempre tratou a *meditação* (hagah) como constitutiva da fé, não como etapa opcional. Há um paralelo entre "subcontratar a escrita" e "subcontratar a devoção" — ambos aleijam a formação do caráter.
- Para quem desenha pipelines e agentes, o alerta prático: o output do seu agente é o que o usuário lê. Se o agente "reescreve" sem critério, está transformando perda líquida de significado. Política de revisão humana não é opcional em documentação crítica.

## Frases notáveis

> "There are no lossless transformations of natural-language text — every rewrite and rephrase changes the meaning of your writing, and if this is done by an entity that doesn't have the most detailed mental representation of what you personally were trying to communicate, information will be lost."

> "Writing is thinking. Spending time on the writing process — on deciding what to emphasize and how to structure your ideas clearly — teaches you more about your topic. If you circumvent this process, you will probably walk away with a poorer understanding of the subject matter."
