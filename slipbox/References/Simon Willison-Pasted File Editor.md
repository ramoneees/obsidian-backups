---
date: 2026-06-02
source: "https://simonwillison.net/2026/Jun/2/pasted-file-editor/#atom-everything"
blog: "Simon Willison"
tags: [ferramentas, web, JavaScript, AI, Claude, Codex]
---
# Simon Willison - Pasted File Editor

## Resumo

Simon Willison compartilha uma ferramenta prática que ele encomendou ao Codex desktop para construir: um editor de texto com a capacidade automática de anexar arquivos a partir de texto colado. A ferramenta foi inspirada pelo comportamento observado no claude.ai, que detecta grandes blocos de texto colados e os converte automaticamente em anexos de arquivo, mantendo a interface limpa e organizada.

O funcionamento é direto e elegante: ao colar um texto com mais de 1000 caracteres no editor, ele automaticamente se transforma em um anexo de arquivo, preservando o conteúdo do textarea principal inalterado. Esse comportamento resolve o problema comum de textareas que ficam lentos ou difíceis de navegar quando contêm grandes blocos de texto.

Além da funcionalidade de colar, a ferramenta também suporta abrir arquivos diretamente no editor — incluindo imagens, que são exibidas como thumbnails — e arrastar arquivos para dentro do textarea. Essa combinação de interações torna a ferramenta versátil para diferentes fluxos de trabalho.

A ferramenta está disponível publicamente em https://tools.simonwillison.net/pasted-file-editor e representa um exemplo interessante de como ferramentas pequenas e focadas, construídas com auxílio de AI, podem resolver problemas pontuais de forma eficaz.

## Pontos Principais
- Ferramenta construída com auxílio do Codex desktop (AI-assisted programming)
- Inspirada no comportamento do claude.ai de converter grandes colagens em anexos
- Texto com 1000+ caracteres colado automaticamente vira um anexo de arquivo
- Textarea principal permanece limpo e inalterado após a colagem
- Suporta abrir arquivos diretamente, incluindo imagens como thumbnails
- Funcionalidade de drag-and-drop para arrastar arquivos ao textarea
- Disponível publicamente em tools.simonwillison.net/pasted-file-editor
