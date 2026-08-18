# Launch Pack + Tend — plano operativo

> Criado: 2026-08-17 (domingo) · Fonte: diagnóstico dos repos `~/dev/pack` (GitHub) e `~/dev/tend` (Gitea/tekton)
> Veredito: pack está a semanas da submissão. tend está a meses — e isso é um design decision, não defeito.

## Frente 1 — Pack iOS → TestFlight (SEMANA 1, resultado visível)

Objetivo: build no TestFlight até sexta.

1. **Verificar contas** — Apple Developer (US$ 99/ano) e Google Play Console (US$ 25) ativas? Os docs do repo assumem que sim; confirmar antes de tudo.
2. **Build local** (sequência crítica, KMM antes de iOS):
   ```
   cd ~/dev/pack/ios && xcodegen generate && pod install
   cd ../shared && ./gradlew :linkDebugFrameworkIosSimulator   # smoke
   # Archive do scheme Pack no Xcode → Distribute App → TestFlight
   ```
   Guia completo: `docs/testflight-guide.md` e `docs/ios-signing-setup.md` (já no repo).
3. **Pós-upload**: TestFlight internal testers → dogfood no iPhone do Boss por 2–3 dias antes de pensar em review externo.
4. **App Store Connect**: criar app, preencher listing a partir de `docs/app-store-listing.md`, review info de `docs/app-review-info.md`.

## Frente 2 — Pack Android (paralela, delegável ao OpenCode/Sisyphus)

1. **Decisão FFmpegKit** (bloqueia o release Android):
   - (a) Dropar AAR manual de mirror (instruções inline em `android/app/src/main/java/com/pack/processing/FFmpegKitExecutor.kt.disabled` e ProcessingModule.kt) — mantém paridade iOS;
   - (b) v1 sem conversão de vídeo (resto funciona) — mais rápido;
   - (c) Migrar pra Media3 Transformer — mais limpo a longo prazo.
   - Recomendação: (a) com fallback (b) se o mirror falhar.
2. **CI vermelho no main**: Android CI + Maestro E2E falharam no último commit 804787e-era (#6, 2026-06-13); o run do PR passou. Investigar se flake ou workflow — provável diferença push vs pull_request.
3. **Secrets**: `gh secret list -R ramoneees/pack` está VAZIO. Release workflow nunca correu de verdade. Criar:
   - `ANDROID_KEYSTORE_BASE64`, `ANDROID_KEYSTORE_PASSWORD` (+ alias/key passwords)
   - Service account Play Console → `PLAY_ACCOUNT_CREDENTIALS` (ou equivalente no workflow)
   - Checklist já existe: `docs/github-secrets-checklist.md`
4. **Play Console**: criar app, listing de `docs/google-play-listing.md`, data safety de `docs/google-play-compliance.md`.
5. Regra do Boss: agentes OpenCode em worktrees separadas; code review (Claude Code ou manual) + dogfood QA depois.

## Frente 3 — Tend (meses; decisão de scope primeiro)

Estado real: 88 ecrãs Expo Router, backend tRPC completo (RLS, realtime, jobs, testes GDPR), adapter Clerk — mas plano MVP com 240 tasks, 0 marcadas; sem infra, sem eas.json, versão 0.0.1, sem Clerk prod.

1. **Decisão de scope antes de qualquer código**: fechar o core loop mínimo — family setup → Today view → routines/tasks → handoffs. Nada de calendar/care-log/check-ins até o loop funcionar com vocês dois.
2. **Infra mínima**: backend → Fly.io (ou equivalente) com Postgres dedicado; Dockerfile ainda não existe no repo.
3. **EAS**: criar eas.json, primeiro build nativo (iOS + Android), expo.dev account.
4. **Clerk produção** + `EXPO_PUBLIC_API_URL` real.
5. **Dogfood obrigatório**: Boss + Chefinha por ≥2 semanas antes de qualquer loja. App de coparenting vive ou morre por dois utilizadores reais.

## Sequência de amanhã (primeiras 2h)

1. Confirmar contas Apple/Google (5 min) — destrava Frentes 1 e 2.
2. Boss decide FFmpegKit: (a)/(b)/(c) — destrava agentes Android.
3. `xcodegen generate && pod install` + archive TestFlight no Xcode (Frente 1).

## Referências rápidas

- pack: `~/dev/pack` · docs de loja em `docs/` · PR #4 review em `review-comments.md` (4/4 blockers iOS resolvidos no #6)
- tend: `~/dev/tend` · `docs/MVP-PRIORITIES.md` (core loop) · `.sisyphus/plans/parenting-platform-mvp.md`
- PRs do tend no Gitea: git.ramoneees.com/tekton/tend

## 2026-08-18 — Pack App Store readiness (executado)

Feito e verificado:
- ✅ Contradição de compliance corrigida (PR #7, merged): PrivacyInfo.xcprivacy agora declara tracking=true + DeviceID/Advertising (realidade AdMob+ATT); copy do ATT e da listing alinhadas; privacy-policy.md v1.1
- ✅ Site obrigatório da Apple no ar: repo público `ramoneees/pack-web` → https://ramoneees.github.io/pack-web/ (support 200, privacy 200, terms 200)
- ✅ Todos os docs de loja apontam para as URLs vivas (commit fd3522d)
- ✅ xcodegen + cocoapods instalados via brew

Pendente (ordem):
1. Build de verificação iOS (rodando; validar depois)
2. Apple Developer account finalizar (Boss) → criar Bundle ID com.pack.app no portal
3. App Store Connect: criar app, listing de docs/app-store-listing.md, IAPs com IDs EXATOS de StoreManager.swift (com.pack.subscription.weekly / .yearly / com.pack.lifetime)
4. Screenshots iPhone 6.9" (guia: docs/ios-screenshots-guide.md) — ainda não existem
5. Archive → TestFlight (docs/testflight-guide.md)
6. AdMob: IDs de Release já são os reais (6873538305991177); conferir se app iOS está registado no console AdMob

## 2026-08-18 — Tend shipping readiness (delegado)

Verificado:
- ✅ Quality gate VERDE no main (typecheck 12/12, test 11/11) — repo muito além do "scaffold" que os docs alegam
- ✅ Core loop substancialmente construído: handoff state machine completo, Today view com "who's on it" lado-a-lado, quick capture, 15 routers, 42 ficheiros de teste
- ✅ AUTH_ADAPTER=static existe → dogfood SEM Clerk prod
- Gap real: nunca correu end-to-end (sem Postgres local, sem .env.example, sem migrations aplicadas, sem deploy)

Agentes OpenCode em curso (worktrees ~/dev/tend-wt-*):
- agent/local-e2e → compose+Postgres16, .env.example, migrations, seed (Boss+Chefinha+dependente+starter kits), runbook local-dev
- agent/deploy-infra → Dockerfile backend, fly.toml (mad), runbook deploy, rec Postgres

Caminho definido: E2E local primeiro (relógio de dogfood 2 semanas Boss+Chefinha começa já, via Expo Go na LAN), deploy em paralelo, eas.json/EAS builds depois do dogfood estabilizar.


## 2026-08-18 (tarde) — Mudança de estratégia (Boss)
- RAM é o recurso escasso (16GB): heavylifting SÓ no pack agora.
- Tend: implementação PARADA (agentes local-e2e/deploy-infra mortos a meio; descobertas preservadas em tend-wt-plan/docs/planning-inputs/). Achado crítico deles: auth adapter static boota VAZIO — nenhum token autentica (fix Wave 0 do plano).
- Tend agora: agente PLANNER (papel prometheus) a gerar .sisyphus/plans/tend-shipping-plan.md (worktree ~/dev/tend-wt-plan, branch agent/shipping-plan). Docs only. Execução depois por sisyphus quando houver folga de RAM.
- Worktrees mortos removidos.


## 2026-08-18 (fim de tarde) — Cadena iOS local VERDE + reviews feitas
- ✅ Xcode 26.6 instalado, license aceita, runtime iOS 26.5 registado (após colisão GUI+CLI que purgou o 1º download — lição: nunca instalar runtime pelas duas frentes)
- ✅ CHAIN COMPLETA LOCAL: KMM framework (linkPodDebugFrameworkIosSimulatorArm64) → pod install (ffmpeg-kit-ios-full 6.0 + GMA) → xcodegen → BUILD SUCCEEDED no simulador iOS 26.5
- ✅ Code review dos 3 PRs: #8 limpo, #9 limpo (só workflows/flows), #10 limpo e bem escrito (executor reescrito c/ coroutine bridge; GPL flag aceito). Ordem de merge: #9 → #10 → #8
- ⛔ NOVO BLOQUEIO: GitHub Actions billing/spending limit esgotado (macOS runners 10x) — TODOS os jobs morrem em 3s. Boss: github.com/settings/billing
- Pendente p/ TestFlight: enrollment Apple ativar → Bundle ID → archive (chain já provada)
- fd3522d = main; PRs #8/#9/#10 draft aguardando billing p/ validação final + merge

## 2026-08-18 (noite) — RUNNER SELF-HOSTED + #9/#8/#12 MERGED (estado atual)

Resolvido nesta sessão (ordem cronológica):
- ✅ Billing destravado; PRs validados e merged: #8 (release pipeline), #12 (piloto Linux Olympus), **#9 (CI triage) — 8/8 verde, merged**. Causa-raiz do crash iOS: `GADApplicationIdentifier` faltando no Info.plist (não era runtime 26.x). Fixes #9: plist key + photo seed + picker confirm.
- ✅ **Runner self-hosted no Mac mini**: `~/actions-runner-osx` (v2.336.0), nohup ./run.sh, log /tmp/mac-mini-runner.log. Fix crítico: `.path` (Java17 brew) + `.env` (JAVA_HOME, DEVELOPER_DIR) — runner boota shell limpo sem PATH. maestro-ios: **2m58s no mini vs 15-17min/10× no GH**. Label: `self-hosted,pack-macos`. Workflow maestro-tests.yml e action ios-kmm-setup já no main (flexíveis c/ runtime/Xcode 26).
- ✅ **PR #10 (FFmpegKit restore) rebasado no main novo (8490de9), pushed, CI a correr** — ver veredito: `gh pr checks 10`. Era 7 commits de CI android (emulator boot budget, daemon cleanup). Stash no worktree pack-wt-ffmpeg guarda o AGENT_BRIEF original da missão ffmpeg (stash@{0}).
- ✅ context_length do Hermes: 500k → 1M (hermes config set) — nova sessão já boota com 1M.

Pickup da próxima sessão (ordem):
1. `gh pr checks 10` → se verde, Boss merge; se ui-test flake, reroll documentado no PR
2. Tend Wave 0 (RAM barata): auth static seed fix — plano em `~/dev/tend` branch agent/shipping-plan, `.sisyphus/plans/tend-shipping-plan.md`; worktree tend-wt-plan
3. TestFlight: enrollment Apple → Bundle ID com.pack.app → archive (chain local já provada)
4. Depois: LaunchAgent p/ runner sobreviver a reboot (1 comando hoje: `cd ~/actions-runner-osx && ./run.sh`)
5. Worktrees pack vivos: pack-wt-ci (#9, merged — removível), pack-wt-ffmpeg (#10), pack-wt-infra
