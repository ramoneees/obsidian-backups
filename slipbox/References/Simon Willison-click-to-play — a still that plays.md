---
title: "<click-to-play> — a still that plays"
source: "Simon Willison's Weblog"
date: 2026-06-17
url: https://simonwillison.net/2026/Jun/17/click-to-play-component/
author: "Simon Willison"
category: "Web Development / Tool"
tags: [web-components, javascript, progressive-enhancement, gif, performance, tools]
ingested: 2026-06-17
---

# <click-to-play> — a still that plays

## Fonte
Simon Willison's Weblog

## Data
2026-06-17

## URL
https://simonwillison.net/2026/Jun/17/click-to-play-component/

## Resumo

Willison lançou uma **Web Component progressiva** que transforma este markup:

```html
<click-to-play>
  <a href="URL to GIF">
    <img src="URL to first frame" alt="...">
  </a>
</click-to-play>
```

Em um still frame com botão click-to-play que carrega o GIF sob demanda. **Pra quando você não quer que GIFs grandes sejam carregados a menos que as pessoas queiram tocá-los.**

**Exemplo de uso** (do próprio post): demonstração das novas ferramentas de edição de linha do Datasette — Willison construiu o Web Component especificamente pra esse post.

**Por que isso importa:**

- Performance: GIFs são notoriamente pesados. Carregá-los só quando o usuário opta reduz drasticamente peso da página inicial.
- Progressive enhancement: funciona sem JavaScript (a `<a href>` para o GIF é fallback) e adiciona a experiência click-to-play quando JS está disponível.
- Acessibilidade: o still frame com `alt` é mais acessível que GIFs auto-playing.
- Reusable: Web Components são framework-agnostic, funcionam em qualquer site.

## Recursos

- [click-to-play component no tools.simonwillison.net](https://tools.simonwillison.net/click-to-play-component)
- [Exemplo em uso (Datasette post)](https://simonwillison.net/2026/Jun/16/datasette/)

## Notas e Conexões

- Willison é conhecido por construir ferramentas pequenas e usáveis. Vale seguir o blog dele.
- Conecta com [[Datasette 1.0a34]] (mesma semana, mesmo autor) — o componente foi construído pra aquele post.
- Padrão de progressive enhancement é battle-tested e deveria ser o default em qualquer site com conteúdo pesado.
- Para projetos próprios de Ramon: se ele for construir conteúdo com GIFs (demos, screenshots animados), esse componente é drop-in.
