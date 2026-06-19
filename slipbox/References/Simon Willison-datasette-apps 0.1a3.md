---
title: "datasette-apps 0.1a3"
source: Simon Willison
date: 2026-06-15
url: https://simonwillison.net/2026/Jun/15/datasette-apps-2/
category: Release
tags: [datasette, release, plugins, permissions, security]
ingested: 2026-06-19
blogwatcher_id: 751
type: beat (release announcement)
---

# datasette-apps 0.1a3

> Simon Willison — beat (release announcement)

## Resumo

Release 0.1a3 do plugin **datasette-apps**. Lançado **3 horas depois da 0.1a2** — mesma data (15 de junho de 2026).

## Mudanças (bug fixes)

- **Bug fix:** usuários sem a permissão `create-app` ainda conseguiam criar apps. Consertado. ([#27](https://github.com/datasette/datasette-apps/issues/27))
- **Bug fix:** era impossível conceder permissão de **editar um app** para usuários que não eram o owner. Regras de edit/delete agora são as mesmas de view: se o app é privado, só o owner pode modificar; caso contrário, permissão controlada pelo sistema de permissões regular do Datasette. ([#29](https://github.com/datasette/datasette-apps/issues/29))

## Notas e Conexões

- Conecta com [[Simon Willison-datasette-apps 0.1a2]] — release anterior do mesmo dia.
- Conecta com [[Simon Willison-Datasette Apps: Host custom HTML applications inside Datasette]] — post principal do lançamento.
- Padrão notável: dois releases em um dia para corrigir bugs de permissão introduzidos na 0.1a2 (mesma janela de 3h). Indica que o surface de attack da sandbox foi pensado com cuidado — não basta rodar `<iframe sandbox>`, tem que garantir que as permissões dentro do Datasette não permitam bypass.
- Link para o release: https://github.com/datasette/datasette-apps/releases/tag/0.1a3
