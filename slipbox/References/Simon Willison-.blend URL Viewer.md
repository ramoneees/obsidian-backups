---
title: ".blend URL Viewer"
source: "Simon Willison"
date: 2026-09-09
url: "https://simonwillison.net/2026/Sep/9/blender-viewer/"
tags: [reference, tools, blender, coding-agents, gpt-6-astra, llms, javascript]
ingested: 2026-09-10
---

# .blend URL Viewer

**Fonte:** Simon Willison's Weblog
**Data:** 9 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/9/blender-viewer/

## Resumo

Novo brinquedo no arsenal Blender+agentes do Simon: um **viewer web para arquivos .blend** (https://tools.simonwillison.net/blender-viewer). Cole a URL de um arquivo .blend acessível por CORS ou link de repo GitHub e ele renderiza a geometria no browser — materiais, iluminação, câmeras salvas de arquivos Blender 5.x, controles de órbita, wireframe e fit.

## Como foi feito (o percurso importa mais que a ferramenta)

1. Gerou a imagem de um **Fabergé egg temático da série Pluribus** com o novo **ChatGPT Images 2.5** (prompt: *"Generate a photo of a faberge egg that's themed after the TV show Pluribus - research first"*).
2. Colou a imagem no **Codex rodando GPT-6 Astra (high)** com o prompt: *"Use your blender local skill to create a blender model of this faverge egg"*.
3. O agente trabalhou **17m51s** e produziu vários `.blend` (repo: simonw/vibe-coded-blender-projects).
4. O viewer já existia como experimento; agora está na coleção tools.simonwillison.net — o modelo renderiza no browser de qualquer pessoa via URL (GitHub resolvido por jsDelivr).

Stats do modelo: 7.2 MB, 387 meshes, 783k vértices, 1.4M triângulos, 17 materiais. Preview aproximado — modificadores não aplicados são omitidos.

## Notas principais

- **Padrão image→3D completo:** imagem generativa → coding agent com skill local de Blender → artefato `.blend` → viewer web compartilhável. Cada etapa usa o output da anterior.
- A skill de Blender local do agente (SKILL.md no GitHub) é a mesma linha do TIL de 5/set.
- Requisito prático do viewer: arquivo em URL **CORS-accessible** ou link de GitHub (resolvido via jsDelivr).

## Conexões

- Continuação direta de [[Simon Willison-Using Blender with coding agents on macOS]] (TIL de 5/set) e do [[resumo-Astra-Pelican-Comparison-Grid-SimonWillison]].
- Tópicos: [[Coding Agents]], [[GPT-6 Astra]], [[Blender]], [[LLM]].
- [[slipbox/References]]
