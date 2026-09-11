---
title: "Datasette 1.0a39 and 0.65.4 security releases"
source: "Simon Willison"
date: 2026-09-11
url: "https://simonwillison.net/2026/Sep/11/datasette-security/"
tags: [reference, simon-willison, datasette, seguranca, ia, auditoria, releases]
ingested: 2026-09-11
---

# Datasette 1.0a39 and 0.65.4 security releases

**Fonte:** Simon Willison (link post → datasette.io)
**Data:** 11 de setembro de 2026
**URL original:** https://simonwillison.net/2026/Sep/11/datasette-security/
**Linkado:** https://datasette.io/blog/2026/september-security-releases/

## Resumo

Duas versões de correção de segurança do Datasette: **1.0a39** (série alpha atual) e **0.65.4** (estável). Aplicar se você roda instância Datasette na web pública — em especial se mistura **tabelas públicas e privadas**.

## O processo é a história

- Issues reportadas por Sevban Dönmez levaram Simon + Alex Garcia a uma **auditoria extensiva usando Claude Fable 5.1, GPT-5.6 e GPT-6 Astra** — quase uma semana colaborando nos fixes.
- Os modelos encontraram bugs **muito** sutis.
- Simon: *"incorporaremos auditorias de segurança por modelos de fronteira em todo o nosso desenvolvimento daqui pra frente."*
- Método de divisão de trabalho do Alex Garcia: num repo privado compartilhado, para cada issue **um criava os testes automatizados que evidenciavam o problema e o outro implementava o fix** — garantindo dois humanos com olhos em cada issue, além dos coding agents rodando modelos diferentes.

## Notas e conexões

- Padrão replicável: auditoria multi-modelo + par humano revisando com testes-antes-fix. Conecta com [[Simon Willison-Quoting huggingface.co-security.txt]] (mesmo dia, mesmo tema de segurança+IA).
- Lembrete prático: instâncias Datasette expostas misturando público/privado = atualizar já.
- [[slipbox/References]]
