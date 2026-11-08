---
title: "datasette #3046: Don't serve link: rel=next HTTP headers to Firefox for HTML pages"
source: https://simonwillison.net/2026/Nov/7/link-rel-next/
date: 2026-11-08
tags: [web, devops, http, firefox]
---

Simon Willison abriu issue no Datasette depois de notar no network panel do Firefox algo estranho: visitar uma página de tabela disparava um prefetch HTTP da próxima página de linhas. O culpado é o header link: rel="next" que o Datasette serve para paginação — o Firefox trata isso como convite e busca a página inteira preventivamente.

O custo é real e silencioso: uma fração minúscula dos visitantes clicaria em "next", mas 100% dos browsers Firefox baixam os dados e o servidor renderiza uma página completa que vai direto para o lixo. Um header inofensivo vira desperdício distribuído de CPU e banda — o tipo de coisa que ninguém nota até olhar o painel de rede.

O melhor do post é o plot twist arqueológico. O bug do Firefox sobre esse comportamento está aberto no Bugzilla há 24 anos. E um dos primeiros comentários desse bug aponta para... um post do próprio blog do Simon, de 2002, reclamando exatamente dessa feature de prefetch do Mozilla. Ele não tinha só esquecido que escreveu sobre isso — tinha esquecido que a feature existia.

É um post de 3 parágrafos que entrega duas lições: (1) auditoria de custos invisíveis vale mais que otimização óbvia — o desperdício estava escondido num header que quase ninguém lê; (2) seu arquivo pessoal é memória externa que às vezes te processa de volta 24 anos depois. Escrever é commit; o blame eventualmente te aponta.

## Por que importa

- Devops puro: um header "padrão" gerando render + fetch desperdiçados em produção. Lembrete de que custo silencioso mora nos detalhes que ninguém revisita.
- A ironia do arquivo pessoal: o blog como vault de longo prazo funcionou — o sistema recuperou um post de 2002 e acusou o próprio autor. Argumento a favor do Obsidian.
- Relíquia da web: bug aberto desde 2002 sobrevivendo a décadas de reescritas do navegador. Débito técnico tem vida útil geológica.

## Frases notáveis

> "their browser is fetching unnecessary data and the Datasette server is having to render an entire page that then gets thrown away"

> "I hadn't just forgotten that I had written about it, I had forgotten the feature entirely!"
