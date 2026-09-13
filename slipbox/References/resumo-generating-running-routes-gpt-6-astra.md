---
title: "Generating running routes with GPT-6 Astra and ChatGPT Work"
source: https://simonwillison.net/2026/Sep/12/astra-running-routes/
date: 2026-09-13
tags: [ia, agentes, openai, geospatial]
---

Simon Willison pediu ao ChatGPT Work com GPT-6 Astra (Max) algo simples: "Moro em <endereço>. Descubra rotas de corrida de 5K e 10K em loop a partir de casa. Use dados do OSM." O agente trabalhou **27 minutos** sozinho e entregou exatamente o pedido — visualização embutida no chat + arquivos GPX e GeoJSON para download. Sem iteração, sem ajuste fino.

O como é mais interessante que o quê: o agente usou **Nominatim** para geocodificar o endereço, **Overpass API** para baixar as vias e trilhas do OpenStreetMap da região, e calculou os loops localmente. Ou seja — não alucinou um mapa, compôs um pipeline geoespacial real com as ferramentas certas de cada etapa. A visualização usou a skill `visualize`: um HTML autocontido com a geometria completa num `<script type="application/json">` e D3 carregado de CDN com allow-list (CSP restrito a cdnjs, esm.sh, jsdelivr, unpkg e fontes).

A crítica de Willison é a parte que importa para quem constrói agentes: **frustrantemente, o código que rodou e os detalhes exatos não estavam visíveis na UI do ChatGPT** — "vejo essa falta de transparência como um anti-feature". E pior: quando pediu uma cópia do código Python depois, o ChatGPT não conseguiu fornecer porque a thread já tinha sido **compactada**. Ele fecha com uma exigência de design: qualquer sistema LLM com compaction precisa preservar o texto pré-compaction e expô-lo via tool calls de agente.

Três lições empacotadas num caso de uso banal: (1) agentes com ferramentas certas resolvem tarefas geoespaciais de ponta a ponta; (2) opacidade de execução é defeito, não feature; (3) compaction que destrói histórico destrói auditabilidade — e agente sem auditabilidade não é delegável.

## Por que importa

- Transparência de execução é critério de compra/delegação: Hermes e agentes locais expõem tool calls; o caso do Willison é o contra-exemplo — ao avaliar stacks de agente (OpenCode, ChatGPT Work), opacidade = não delegável para trabalho sério.
- O bug da compaction é diretamente relevante para sessões longas de agentes (worktrees, pipelines longos): histórico preservado e acessível é requisito, não luxo — senão o "porquê" do resultado some.
- 27 minutos de trabalho autônomo com composição de ferramentas (Nominatim + Overpass + cálculo local + skill de visualização) é o benchmark do que "tarefa delegável" virou: multi-etapa, multi-ferramenta, resultado verificável.

## Frases notáveis

> "I see this lack of transparency is an anti-feature."

> "I think any LLM system that uses compaction needs to both preserve the pre-compacted text and make that text available via agent tool calls, to protect against this kind of problem."
