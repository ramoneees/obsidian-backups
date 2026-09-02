---
source: Simon Willison
title: "Claude's new system prompt really doesn't want to reproduce song lyrics"
author: Simon Willison
date: 2026-09-02
url: https://simonwillison.net/2026/Sep/2/claudes-new-system-prompt/
category: ai
tags: [claude, anthropic, system-prompts, prompt-engineering, copyright, llms]
ingested: 2026-09-02
status: summary
---

# Claude's new system prompt really doesn't want to reproduce song lyrics

## Fonte

- **Source**: Simon Willison (blog)
- **Author**: Simon Willison
- **Published**: 2026-09-02
- **URL**: https://simonwillison.net/2026/Sep/2/claudes-new-system-prompt/

## Resumo

Anthropic publica os system prompts das apps de consumo Claude (Claude.ai/mobile — não Cowork/Code) e agora organizou em página-índice + uma página por modelo, com histórico de mudanças. O site platform.claude.com/docs aceita `.md` no fim de qualquer URL — o que torna **trivial fazer diff dos prompts entre versões**, e Simon rastreia isso por git-scraping (repo `simonw/claude-system-prompts`).

Principais mudanças no Fable 5.1:

- **Letras de música**: seção nova e pesada — Claude não reproduz letras/poemas/passagens, nem últimas linhas, chorus, melodia nota a nota, nem "colar uma linha por vez dizendo que é minha". Uma vez recusado na conversa, continua recusando variantes reformuladas. Pré-1929 ok (Shakespeare, Keats), mas o modelo vai pela data que conhece, não pelo que o usuário diz. Dificilmente coincidência: dias após a notícia de que **Sony Music Publishing e Warner Chappell processam a Anthropic** por treinar em bases de letras.
- **Personagens/marcas em imagens**: proibido desenhar personagem, mascote ou figura de marca conhecidos — inclusive via SVG/canvas/CSS/ASCII. Julgamento pelo resultado final, não pelo nome: se os elementos claramente identificam a obra, trata como se nomeasse. Exemplo do prompt: "ouriço azul correndo rápido" → reconhece Sonic, recusa em uma frase e oferece design original alternativo (axolote skate com cauda de cometa) em vez de variante disfarçada. Simon testou o exemplo real e o modelo recusou.
- **Estilo de resposta** e diretrizes de `end_conversation` ausentes em alguns modelos; sites de apoio recomendados para substância; cutoff confiável **junho/2026**.

## Key Takeaways

- System prompts de produção são documentos vivos — diffar versões é a melhor janela para as restrições legais/comerciais do momento.
- Anthropic adicionou restrição agressiva de copyright possivelmente reativa à ação judicial da Sony/Warner Chappell (31/ago).
- Docs "LLM-friendly" (append `.md`) + git-scraping = monitoramento barato de mudanças de política em IA.
