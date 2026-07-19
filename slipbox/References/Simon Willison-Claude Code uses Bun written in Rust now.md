---
title: "Claude Code uses Bun written in Rust now"
source: Simon Willison
author: Simon Willison
date: 2026-07-19
ingested: 2026-07-19
url: https://simonwillison.net/2026/Jul/19/claude-code-in-bun-in-rust/
category: tools
tags: [claude-code, bun, rust, anthropic, simon-willison]
---

# Claude Code uses Bun written in Rust now

> "Claude Code v2.1.181 (released June 17th) and later use the Rust port of Bun. Startup got 10% faster on Linux but otherwise, barely anyone noticed. Boring is good."

## TL;DR

Willison confirma empiricamente que Claude Code v2.1.181+ está rodando o **port Rust do Bun** em produção, em milhões de dispositivos. A performance é praticamente a mesma ("barely anyone noticed") — o que é o melhor cenário para uma troca de runtime em larga escala. **"Boring is good"** é o critério de Jarred Sumner (autor do Bun).

## Como Willison verificou

### Comando 1: versão do Bun embarcado

```bash
strings ~/.local/bin/claude | grep -m1 'Bun v1'
```

Output dele: `Bun v1.4.0 (macOS arm64)`. O release mais recente do Bun no GitHub era v1.3.14 (12 de maio). A v1.4.0 no Claude **suporta a tese de que eles estão shippando uma preview ainda não released**.

**Update**: a versão Rust _já foi_ released como **Bun canary**. Rodar `bun upgrade --canary` instala a release.

### Comando 2: nomes de arquivos `.rs`

```bash
strings ~/.local/bin/claude | grep -Eo 'src/[[:alnum:]_./-]+\.rs'
```

Output: lista de **563 nomes de arquivo** .rs (gist público: [gist.github.com/simonw/c92fb0f67b114ac26e3b95a09ddccfdc](https://gist.github.com/simonw/c92fb0f67b114ac26e3b95a09ddccfdc)), começando com:
```
src/runtime/bake/dev_server/mod.rs
src/runtime/bake/production.rs
src/bundler/bundle_v2.rs
```

Confirmação: **Bun in Rust está realmente rodando em produção** através do Claude Code.

## Update de Ajan Raj (truque esperto)

```bash
cat > /tmp/bun-version.ts <<'EOF'
console.log("embedded bun:", Bun.version);
process.exit(0);
EOF
BUN_OPTIONS="--preload=/tmp/bun-version.ts" claude --version
```

Output: `1.4.0`. **Commit de 17 de maio** ([commit b18bf6d](https://github.com/oven-sh/bun/commit/b18bf6d1d0a92238f240bfd125f0e3b3461b9243)) que atualizou a versão em `package.json` para 1.4.0. Não mudou desde então, mas também **não chegou a um tagged release fora de `canary`**.

## Por que importa

- Anthropic está comfortablemente shippando runtime novo (Bun-Rust) em produção para milhões de usuários
- Startup 10% mais rápido em Linux — pequeno mas mensurável
- "Boring is good" — o melhor sinal de uma migração de runtime bem feita é ninguém perceber

## Notas e Conexões

- Tags Willison: `rust`, `anthropic`, `claude-code`, `bun`, `jarred-sumner`
- Willison fez um [gist público](https://gist.github.com/simonw/c92fb0f67b114ac26e3b95a09ddccfdc) com os 563 nomes de arquivo `.rs`
- Conexão com [[Claude Code]] — tipo de agent que Ramon usa via Hermes
- Conexão com [[Hermes Agent]] — pode estar rodando o mesmo runtime
