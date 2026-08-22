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

## 2026-08-18 (noite 2) — Billing RE-bloqueado; PR #10 validação JVM local

- ⛔ GitHub billing morto de novo: TODOS os jobs `ubuntu-latest` morrem em 2-3s ("payments failed or spending limit"). Repo pack é PRIVATE → Linux minutes bill. 2ª vez; provável causa: runs macOS 10× da validação de ontem.
- ✅ Self-hosted ambos ONLINE e verdes: olympus-mac-mini (maestro-ios 3m18s no PR #10) + olympus-pack-1 (ci.yml pilot success no main). PR #10 está MERGEABLE — só falta sinal de CI.
- 🔍 Runner Linux (pack-runner pod, k3s, 4CPU/10Gi) é NU: sem Java, sem Android SDK, sem KVM → leva jobs JVM após provisionar setup-java/gradle; emulator jobs (ui-test, maestro-android) NUNCA lá.
- ✅ Validação local em curso no worktree pack-wt-ffmpeg (comandos idênticos ao CI, --no-daemon): lint → kmm-compile → test (unit+jvm) → assembleDebug. Se verde → #10 tem veredito sem gastar cêntimo.
- Decisão pendente Boss (5 min): github.com/settings/billing — payment method falhou ou limit consumido? Alternativa $0: migrar os 6 jobs ubuntu-latest → runner Linux (JVM jobs c/ setup-java) e/ou mini (emulator jobs c/ imagem arm64).
- Ordem dos merges permanece: #10 verde → merge → depois #13+ (retarget workflows).

## 2026-08-18 (noite 2, cont.) — Android SDK no mini; validação JVM parcial verde

- ✅ Android SDK instalado no mini via brew cask android-commandlinetools (ANDROID_HOME=/opt/homebrew/share/android-commandlinetools; 5.8GB: platform-34, build-tools 34, platform-tools, emulator, sysimage arm64-v8a google_apis). Licenças aceitas.
- ✅ `ANDROID_HOME` acrescentado ao `~/actions-runner-osx/.env`; runner REINICIADO e online — mini agora faz iOS + Android (emulator via Hypervisor.framework, sem KVM).
- ✅ Validação local PR #10 (pack-wt-ffmpeg): compileKotlinJvm + jvmTest VERDES. Suite completa (lint→kmm-android→test→assembleDebug) a correr com SDK.
- Lição: brew openjdk@17 não é symlinkado no JVM registry do macOS — `/usr/libexec/java_home -v 17` retorna vazio; usar o path literal do runner .env.
- Próximo: suite verde → Boss merge #10 → PR retarget (ubuntu-latest → self-hosted) baseado no main novo.
- ✅ Runner mini agora é LaunchAgent (`./svc.sh install`+start → `actions.runner.ramoneees-pack.olympus-mac-mini`, KeepAlive, reboot-proof). Logs mudaram para `_diag/ActionsRunnerService_*.log`; `/tmp/mac-mini-runner.log` obsoleto. Pickup item 4 fechado.

## 2026-08-18 (noite 2, fim) — PR #13: pipeline 100% self-hosted

- ✅ **PR #10 MERGED** (20:55Z, merge 8490de9→0159343) após validação local $0: kmm/test/build verdes, maestro-ios verde no mini, lint 2 erros pre-existing do PR #5 (SettingsScreen API-33 vs minSdk 26; non-blocking por design — follow-up próprio).
- ✅ Android SDK 5.8GB instalado no mini (platform-34, build-tools 34, emulator, arm64-v8a image). Emulator Android no macOS = Hypervisor.framework (sem KVM).
- ✅ **PR #13 aberto**: todos os jobs ubuntu-latest → self-hosted. Android (10 jobs) → pack-macos; kmm-tests → pack-linux (mantém setup-java; pod nu). Emulator jobs: arm64-v8a/api-34, steps Linux-only removidos (KVM udev, disk-fencing). Fix extra: GNU `sed -i` → BSD em android-release. setup-java dropado nos jobs macOS (JDK17 via .env do runner).
- ⛔→✅ Bug do LaunchAgent: `.path` multi-linha virava PATH inválido no boot launchd → "tar: command not found" no JobExtension (jobs morriam em 5s). Fix: `.path` = 1 linha colon-separated + restart svc. Antes funcionava por sorte: boot nohup herdava PATH rico do shell.
- Estado no fecho da sessão: 7 jobs do PR #13 re-queued no mini corrigido (~30-45min serial, $0). Ver veredito: `gh pr checks 13`.
- Pendente: billing GitHub continua quebrado (irrelevante p/ CI pack agora, relevante p/ outros repos); follow-up lint SettingsScreen (2 erros API-33); tend Wave 0 brief pronto em tend-wt-plan/AGENT_BRIEF.md (falta go).

## 2026-08-19 (manhã) — PR #13 MERGED 7/7; prometheus entrega spec Wave 0

- ✅ **PR #13 merged** (08:17Z, main 9c86e88): pipeline pack 100% self-hosted. Board final 7/7 verde (ui-test 6m25s c/ emulator arm64 real; maestro-ios 3m9s pós-fix LANG). Billing GitHub tornou-se irrelevante p/ pack.
- ✅ Fixes da noite em 3 camadas: `.path` colon-sep (tar), `.env` +LANG (CocoaPods), emulator arm64/api-34 (QEMU recusa x86_64 em host aarch64).
- ✅ **prometheus (opencode) completou spec Wave 0**: `.sisyphus/plans/wave0-static-auth-spec.md` (646 linhas, verificado contra código). Drift crítico: backend STRIP `AUTH_ADAPTER_OPTIONS` (zod env schema não declara; index.ts passa env limpo) — factory fix sozinho teria boot-crashado; spec inclui passthrough em env.ts. Outros: teste existente codifica o bug (factory.test.ts:10-14 → reescrever c/ allowEmpty), testes já existem em tests/unit/, zod já é dep. Bônus W5: CLERK_SECRET_KEY/ORY_BASE_URL sofrem strip igual.
- Próximo tend: sisyphus executa a spec (aguarda go — RAM ok, pack CI não precisa do Mac). Next pack: enrollment Apple → Bundle ID → archive TestFlight (Boss); hygiene PRs (lint SettingsScreen, smoke instrumentado, screenshots 6.9") delegáveis.

## 2026-08-19 (meio-dia) — WAVE 0 DONE (sisyphus, verificado independente)

- ✅ 1ª run sisyphus STALOU após escrever testes red (2h, 6min CPU — vs 1m15s na resume run sã; watchdog: mtime de ficheiros + CPU do PID). Kill limpo, trabalho red preservado, resume run reconciliou.
- ✅ **Wave 0 completo**: b27e113 (21 testes factory + 2 env, TDD red 8+1 verificado) → 07bc705 (factory zod seed + env.ts passthrough + .env.example). Gate 25/25, backend 388/388, auth-adapter 31/31 — corridos pelo Hermes independentemente.
- ✅ Desvio documentado e ENDORSED: spec §3.1 contraditória (mensagem de erro recomenda {"allowEmpty":true} que o schema rejeitava); fix 1 token `.default([])`; nota em .sisyphus/evidence/wave0-0.2-deviation-note.md.
- Nota env: worktree tend-wt-plan não tinha node_modules (planner só docs); sisyphus symlinkou os 8 dirs de ~/dev/tend (lockfiles byte-idênticos verificados). Symlinks untracked — ficam.
- Lição stalled-run: quando opencode run fica >30min sem tocar ficheiros e CPU ~0 → kill + resume c/ brief de reconcile; não esperar.
- **Pendente Boss: push de agent/shipping-plan p/ Gitea** (sem creds locais — confirmado). 3 commits à espera: spec prometheus + wave0 ×2.
- Próximo: prometheus spec Wave 1 (local E2E: compose pg16.4, migrations, seed, runbook) → sisyphus build. Docker 29.4 + imagem postgres já verificados locais.

## 2026-08-19 (tarde) — MAX PLAN anual; modo fleet; W1 build + W2 spec em paralelo

- ✅ Boss fechou **GLM Coding Plan Max anual** (~$112/mês). Hermes, OpenCode e Claude Code estão TODOS na lista oficial de tools suportadas (docs.z.ai/devpack/tool/others). Endpoint: api.z.ai/api/coding/paas/v4 (já era o do LiteLLM). Novo plano pós-Jul/30 é credits-based; 5.3/5-turbo custam 3× em peak 07:00-11:00 LIS — rota 4.7 de manhã fica barata. Key nova testada end-to-end via LiteLLM (HTTP 200).
- ✅ **Wave 1 spec pronta** (898bba6, 641 linhas, 10 drifts: 11 migrations não 12; sem tabela households; task.list exige familyId; roles real FAMILY_ADMIN/PARENT; seed via withUserContext RLS-proven). Sisyphus build em curso (evidence TDD-red já aparece).
- ✅ Prometheus WAVE 2 spec em paralelo (brief em AGENT_BRIEF_W2.md separado — W1 intacto durante build; planner read-only).
- ✅ **PR #14 aberto** (pack): fix lint SettingsScreen API-33 (agent + verificação independente: 0 erros, 135/135 testes). Branch ci/lint-settings e802553.
- Doutrina fleet (Max plan): **planners ilimitados (só API), builders racionados por RAM**. Watchdog: >30min sem mtime/CPU ~0 → kill + resume c/ brief de reconcile.
- Queue: W1.5 Expo Go dogfood · W3 EAS specs · pack smoke instrumentado + screenshots 6.9" · store listings.
- Desk Boss: push Gitea tend (4 commits) · enrollment Apple · Play secrets.

## 2026-08-19 (tarde, cont.) — Inventário GLM Max via LiteLLM + roteamento por custo

- Probe empírico (1 request/modelo): **LIVE (11)**: glm-5.3, 5.1, 5, 5-turbo, 4.7, 4.6, 4.5, 4.5-air, 4.5-flash, 4.7-flash, 4.5v, 4.6v. **MORTOS no plano**: glm-4.7-flashx (exige saldo API), glm-5v-turbo (excluído da tier).
- Roteamento oficial: sisyphus/prometheus/code-review=**5.3** (3× peak 07-11h LIS; correr de noite=1×) · micro-agentes (lint, renames, docs)=**4.7** via `--model` no launch · cron/briefings/watchdogs=**4.5-flash/air** · visão (screenshots QA)=**4.5v/4.6v**.
- Liturgia dos briefs: agente one-shot NUNCA termina turno à espera de subagent (sem notificações = deadlock). Prometheus W2 caiu nisso; resumido c/指令 explícita.
- PR #14: 6/7 verde (lint PASS em CI 38s — fix confirmado ponta-a-ponta).

## 2026-08-19 (fim de tarde) — PR #14 MERGED; omo.jsonc remapeado GLM-only; W2 spec pronta

- ✅ **PR #14 merged** — lint pack limpo no main pela 1ª vez desde Junho.
- ✅ **~/.omo/omo.jsonc remapeado** (backup .bak.before-glm-remap-20260819): sisyphus/hephaestus/prometheus=5.3 · oracle/metis/momus=5.2 · librarian/explore/atlas/junior/quick/writing=4.7 · multimodal-looker=gemini-2.5-pro (única exceção: plano GLM sem visão no opencode). Antes: 6 agentes ainda em qwen/minimax/deepseek. Default global opencode = zai-coding-plan/glm-4.7. Mecanismo verificado: `-m zai-coding-plan/glm-4.7` (banner confirma); `--agent` é ignorado em run mode.
- ✅ **W2 deploy spec** (5ea108e, 772 linhas): Dockerfile root-context, fly.toml tend-api/mad, auto_stop_machines=off p/ pg-boss, RLS bootstrap SQL, 13 passos c/ 4 Boss-gates. Drift crítico: `fly postgres attach` cria user SUPERUSER por default → spec usa `--superuser=false` + grants (guardrail RLS preservado). Risco nº1: pnpm filtered-install no Docker (por isso o gate de build local é barreira antes dos gates pagos).
- Sisyphus W1 a meio (step ~6/14; evidence: tdd-green, migrate, seed, force-rls já em disco).
- ✅ **Push Gitea feito + PR #7 aberto** (tekton/tend, agent/shipping-plan → main): W0 impl + specs W1/W2. Aguarda merge do Boss. Creds: token one-shot na URL (remote limpo), PR via API c/ GITEA_HERMES_TOKEN.
- 📋 **Apple Enrollment SUBMETIDO, em processamento** (ID R7L6463M9A, ramonp.rios@gmail.com, 2026-08-19). Típico 24-48h; às vezes telefone de verificação. Ao ativar: aceitar agreement → Bundle ID com.pack.app → app record → archive (chain local provada) → TestFlight. Pre-staging possível sem conta: screenshots 6.9" via simulador (queue após W1).

## 2026-08-19 (noite) — WAVE 1 DONE (sisyphus, verificado + lições de verificação)

- ✅ **Wave 1 completo**: 4 commits (b68128d compose → b9402cf TDD red → ce68672 migrate+seed RLS → 4e00c0a runbook/evidence). Gate 12/12, 7/7, 392/392. E2E provado: task.list autenticado (token Boss 200 c/ dados reais, Chefinha 200, sem token 401). Compose down, volume preservado, portas livres — estado final limpo.
- **Bônus do build**: D15 reparou bug REAL pre-existing (task.list SELECT de 3 colunas sem migração — criou 0012 repair; migrate agora = 12) + D14 boot blocker (rrule ESM interop). 8 desvios documentados em .sisyphus/evidence/wave1-deviations.md.
- Lição de verificação (minha): errei 2× ao validar — POST em query tRPC (é GET) e re-run de migrate não-idempotente (D18 documentava; uso `db:reset` p/ re-seed). Além disso: resolver módulos pelo path do checkout principal (tend/) engana — sempre cd ao worktree. Evidência do sisyphus era correta.
- **Branch agent/shipping-plan agora: 8 commits à frente do main** (W0+W1+specs). PR #7 Gitea atualiza-se sozinho no push (mesma branch).
- Próximos passos: (a) push dos 4 commits W1 → PR #7 cresce; (b) Expo Go 2 phones (passos 10-11 do spec W1 — runbook docs/runbook/local-dev.md tem o procedimento; precisa Boss + Chefinha fisicamente); (c) W2 build (Dockerfile/fly) até aos Boss-gates.

## 2026-08-19 (noite II) — PR #7 MERGED; Play armado; W2 build DONE @ BG-1; keystore regen

- ✅ **PR #7 (tend) MERGED** (539e19d): W0+W1+specs no main. Remote do checkout ~/dev/tend agora token-wired (pull ok).
- ✅ **Play Console armado** (Boss): SA `id-pack-android-publisher@pack-500912` criada (org policy disableServiceAccountKeyCreation contornada — Boss é owner, desligou/criou chave), convidada com permissão release internal; projeto pack-500912 linkado. Secrets GH: GOOGLE_CLOUD_CREDENTIALS_JSON + keystore ×4 + var ANDROID_PACKAGE_NAME=com.pack.app. JSON temp destruído após seed.
- ✅ **PR #15 merged** (R8 LoudnessCodecController dontwarn; AAB local 25MB provado).
- ⛔→✅ **Keystore incidente (meu)**: keytool PKCS12 NÃO suporta store/key passwords diferentes — key usava store-pw silenciosamente; secretei key-pw distinta → signReleaseBundle "final block not properly padded". Regen com password ÚNICA, secrets resetadas, v1.0.0(3) disparada. Lição: PKCS12 = 1 password, sempre.
- ✅ **W2 build DONE até BG-1** (sisyphus, 4 commits, Docker gate local PASSOU — image 1.68GB kept; fix D-9 COPY gap que mascarava localmente). Branch agent/wave2-deploy pushed, **PR #8 Gitea** aberto. BG-1..4 (flyctl/auth/create/deploy) = Boss, runbook docs/runbook/deploy.md.
- Pendente: v1.0.0(3) run em curso (sign+upload internal); 1Password update c/ nova keystore password (arquivo ~/pack-keystore-creds.txt até Boss copiar; depois shred).

## 2026-08-19 (noite III) — 🎉 PACK v1.0.0 NO GOOGLE PLAY (internal) · Tend W2 MERGED

- ✅ **pack v1.0.0(3) NO PLAY, internal track**: build-release SUCCESS (sign com keystore nova) + deploy-internal SUCCESS (SA upload). promote-production failure = stub documental (gcloud não instalado no mini; só instruções — design). Próximo Boss: Play Console → Internal testing → opt-in link → instalar no telemóvel; juntar 20 testers p/ clock 14 dias.
- ✅ **Tend PR #8 (W2 infra) MERGED** (2f12732). BG-1..4 fly (auth/create/postgres+attach --superuser=false/deploy) prontos quando Boss quiser — runbook docs/runbook/deploy.md.
- Estado global dos launches: pack Android = internal LIVE · pack iOS = à espera Apple enrollment (R7L6463M9A) · tend = W0/W1/W2 code DONE, falta BG fly + Expo Go dogfood 2 semanas (Boss+Chefinha) · EAS/W3 specs = queue.

## PICKUP — tend rumo a "produto pronto" (definido 2026-08-19 noite)

1. **API live — Boss, 1 tarde**: BG-1..4 do runbook (docs/runbook/deploy.md): `brew install flyctl && fly auth login` → `fly apps create tend-api` → `fly postgres create tend-db --region mad` → **`fly postgres attach tend-db -a tend-api --superuser=false`** (guardrail RLS) → bootstrap SQL §6 spec W2 → `fly secrets set` (checklist runbook) → `fly deploy -c apps/backend/fly.toml` → seed + verify (step 12). ~$2-3/mês.
2. **App instalável — W3 (agentes, 1-2 dias)**: ainda NÃO começado. Prometheus spec → sisyphus build: eas.json, conta expo.dev (Boss, free tier), bump 0.0.1→0.1.0, builds EAS apontados à API live. iOS depende do enrollment Apple (partilhado c/ pack).
3. **Dogfood gate — W4 (2 semanas calendário, incompressível)**: Boss+Chefinha uso diário real. PODE COMEÇAR CEDO: Expo Go contra backend local (runbook local-dev.md) antes de fly/EAS — clock oficial re-corre contra API deployed, mas fricção óbvia já resolvida.
4. **Store polish — W5 (agentes 2 dias + clicks Boss)**: privacy manifest, policy/terms hosting (pattern pack-web), listings, screenshots. **Decisão Clerk**: ship c/ static ou cut to Clerk prod — e W5 DEVE estender env.ts p/ CLERK_SECRET_KEY (mesmo bug strip do W0; senão Clerk boota morto).
5. Dívida não-bloqueante: image Docker 1.68GB (cosmético; fix `pnpm deploy` notado W3+); migrate não-idempotente (documentado; db:reset provado).

Próximo comando da máquina: "prometheus W3 spec" quando Boss der go.

## 2026-08-20 (manhã) — T1 mystery resolvido; sisyphus T1-resume + prometheus W3 spec lançados

- 🔍 **Run fantasma T1 descodificado**: 2026-08-19 22:30-22:46, verificação mobile E2E (db reset→migrate 12→seed→RLS→boot→health→tRPC auth→expo config TUDO verde) que morreu a diagnosticar **skew Metro**: root 0.81.5 vs hoisted 0.84.4 (@react-native/metro-config@0.86.0 nested) + metro-cache-key 0.84.4. Sem conclusão/commits; evidence t1-* no checkout principal. Stray: apps/mobile/package.json modificado no checkout principal (scripts android/ios → expo run:*) — não commitado, deixado.
- 🚀 **sisyphus T1-resume** lançado (proc_56befa76496f, worktree tend-wt-t1, branch agent/t1-mobile-verify, brief AGENT_BRIEF_T1.md): reproduzir erro de bundle via expo export → fix skew (preferência: alinhar à linha 0.81.x do expo 52) → provar export iOS+Android + expo start responde → smoke backend pairing → gate verde. Destrava dogfood Expo Go.
- 🚀 **prometheus W3 spec** lançado em paralelo (proc_cd1990239a9f, worktree tend-wt-plan, branch agent/wave3-eas, brief AGENT_BRIEF_W3.md): eas.json, bump 0.1.0, Android-first (iOS gated no enrollment R7L6463M9A), credenciais/keystore próprio tend, free-tier limits verificados. Docs only.
- Ambos a 5.3 em janela peak (07-11h, 3× quota) — decisão de prosseguir foi do fluxo. Watchdog usual: >30min sem mtime/CPU~0 → kill+resume.
- Estado: RAM 71% livre no lançamento; flyctl ainda NÃO instalado (BG-1..4 continuam na mesa do Boss, ~1 tarde).

## 2026-08-20 (manhã, cont.) — sisyphus T1 morreu por DB lock; site pitch tend LIVE no cluster

- ⛔ **sisyphus T1 falhou no arranque**: "database is locked" — dois `opencode run` simultâneos competem pelo DB local; prometheus segurou o lock. Lição: **1 opencode run de cada vez** (ou sequenciar launches). Resume quando prometheus entregar. Brief preservado em tend-wt-t1/AGENT_BRIEF_T1.md.
- 🎉 **tend.ramoneees.com LIVE no cluster** (pitch site p/ amigo/candidato a sócio): Claude Code (conta claude.ai própria, sem colisão c/ opencode) construiu 1 página pt-PT 15KB (design system exato: creme #FAF6F1, terracota #D97757, sem pedidos externos); wiring Hermes: apps/tend-website/ no olympus (padrão pack-website: ConfigMap+nginx:alpine 32Mi, IngressRoute, commit 59f7eca) → Flux → HTTPS 200, TLS ok, gzip 15KB→5KB. Fonte: ~/dev/tend-website/index.html.
- ⛔ **Acesso externo pendente (Boss, 2 min)**: tend.ramoneees.com NÃO resolve fora de casa (wildcard só interno via AdGuard). Caminho de casa: tunnel weserve-tunnel (cloudflared) já serve packapp publicamente. Boss: CF Zero Trust → Tunnels → weserve → Public Hostname `tend` → http://tend-website.apps.svc.cluster.local:80. Sem token CF API no ambiente Hermes.
- Prometheus W3 spec ainda a correr (validando free tier EAS: 15+15 builds/mês, queue 90+min, verificado contra docs.expo.dev).

## 2026-08-20 (tarde) — W3 spec ENTREGUE+verificada; GAP crítico confirmado; sisyphus T1 r2 lançado

- ✅ **W3 spec entregue** (65bb9cc, 527 linhas): eas.json 4 perfis, android-first (BG-5..8), credentials matrix, drift 9 entradas. Free tier EAS verificado: 15+15 builds/mês, queue low-priority 90+min, timeout 45min, 1 concorrência.
- ✅ **Hermes verificou os 2 GAPs críticos da spec contra o código real**: GAP-1 REAL — client.ts httpBatchLink sem header Authorization (só realtime.ts:336 WS autentica) → todas as queries tRPC protegidas 401 pós-login; qualquer build/dogfood morria no 1º ecrã. GAP-2 REAL — design-tokens exports apontam a dist/ gitignored → fresh install (EAS cloud) falha resolução.
- 🚀 **sisyphus T1 r2** (proc_4cb0ae97707d, tend-wt-t1): brief ampliado — passo 0 = GAP-1 em TDD (client.test.ts header test) + design-tokens fix, depois Metro skew + expo export proof. DB lock livre (prometheus terminou antes de lançar).
- Lição confissão: entrega de agente às 10:29 + interrupção do user = spec ficou 3h sem verificação independente. Regra já conhecida reforçada: verificar na hora, mesmo com context switch.

## 2026-08-20 (tarde II) — PR #9 (T1) ABERTO; Fly BG-1..4 executados pela máquina; API deploy em curso

- ✅ **T1-r2 DONE + verificado + PR #9 aberto** (https://git.ramoneees.com/tekton/tend/pulls/9, agent/t1-mobile-verify): GAP-1 auth header TDD (smoke: Boss 200/4tasks, Chefinha 200/4tasks, no-auth 401), GAP-2 design-tokens repoint src/ (elimina classe fresh-install), metro 0.81.x overrides. Export EXIT=0 ios/android/web; metro serving; gates 25/25+11/11. 5 commits. Review note: TODO obsoleto em client.ts (menciona @tend/api-client que já existe como contracts) — cosmético. AGUARDA MERGE BOSS.
- ✅ **Fly BG-1..3+5 DONE pela máquina** (Boss criou conta + deu token): app tend-api criada (org personal) · postgres tend-db **região cdg NÃO mad — mad foi extinta do Fly; drift real apanhado na execução** · attach --superuser=false (user tend_api) · bootstrap RLS via fly proxy 15433→5433 + psql docker (verificação exata à spec: tend_api f, f, t; app_admin único BYPASSRLS) · secret AUTH_ADAPTER_OPTIONS staged (linha local ≡ prod, ids fixos).
  - Lições: psql via `fly postgres connect < file` pendura SEM executar em non-TTY mas EXECUTA (re-run idempotente provou); PGPASSWORD export não atravessa docker run — usar -e; fly proxy -a tend-db (não -a tend-api sem máquinas).
  - Creds: ~/.fly-token-tend + ~/.fly-tend-db-creds.txt (0600; senha superuser pg para 1Password do Boss; depois shred).
- ⚠️ **Deploy r1 FALHOU, drift flyctl**: v0.4.86 resolve dockerfile/ignorefile relativos ao CONFIG (apps/backend/), não ao CWD → path duplo + .dockerignore ignorado (contexto 830MB c/ node_modules). Fix no checkout principal: fly.toml dockerfile="Dockerfile" + .dockerignore copiado a apps/backend/. **Deploy r2 em curso** (proc_5d3c5f9690b1). Commit do fix pendente (após deploy verde, junto c/ evidence).
- Próximo após deploy verde: seed prod (fly ssh console node dist/scripts/seed.js) → verify §8 (health/ready/trpc+RLS proof) → board + commit fixes → BG fechado, API LIVE.

## 2026-08-20 (tarde III) — 🎉 TEND API LIVE EM PRODUÇÃO (tend-api.fly.dev)

- ✅ **API LIVE**: https://tend-api.fly.dev — health ok · ready/database connected · tRPC task.list autenticado 200 c/ dados seed (Boss token) · no-auth 401 · **prova RLS: app_user vê 0 rows sem contexto tenant, 4 com** (evidence w2-golive-*.txt). Deploy final verde: release_command (12 migrations+RLS) ok, 2 máquinas cdg, imagem 180MB.
- ✅ **Seed prod aplicado**: família completa (1 família, Boss+Chefinha, 1 dependente, 2 rotinas, 4 tasks, 1 handoff, 8 audit rows). AUTH_ADAPTER_OPTIONS secret já estava staged (linha local ≡ prod).
- ✅ **PR #10 aberto** (fix/fly-deploy-drift): flyctl v0.4 path semantics + mad→cdg + evidence golive. Com o PR #9 (T1 mobile) = **2 PRs à espera de merge do Boss**.
- ⚠️ Deploy r2 também falhou antes do verde: primary_region mad extinto (release_command não provisiona) — 3ª correção da tarde. Custo total dos drifts: 2 deploys falhados, zero dados perdidos.
- Fly creds: token + senha pg superuser em ~/.fly-*.txt (0600) — **Boss: copiar p/ 1Password e depois shred**. Conta: org personal "Ramon Rios", cartão on file.
- Postgres: tend-db cdg, unmanaged 256MB+1GB vol, ~$2.2/mês + API ~$2-3/mês. Budget dentro do previsto ($4-5/mês runbook).
- **Dogfood agora possível contra PROD**: EXPO_PUBLIC_API_URL=https://tend-api.fly.dev/trpc (substitui LAN IP quando quiserem testar fora de casa). Falta merge PR #9 (GAP-1) para o mobile autenticar direito.

## 2026-08-20 (fim de tarde) — PRs #9/#10 MERGED; W3A entregue → PR #11; dogfood armado

- ✅ **#9 e #10 merged pelo Boss** (main ab31c1c). Worktree t1 removido. apps/mobile/.env → apontado a https://tend-api.fly.dev/trpc; Metro a servir :8082 (expo start, proc gerido) — Expo Go dogfood pronto nas 2 phones (QR no terminal).
- ✅ **W3 Phase A DONE+verificado** (sisyphus, branch agent/wave3-eas, 3 commits): eas.json 4 perfis, 0.0.1→0.1.0, expo-dev-client ~5.0.20 (linha SDK-52; fallback 4.0.29 doc.), expo-updates dangling config removida, docs/runbook/eas-builds.md. Export ios+android EXIT=0 3.9MB Hermes, fly URL inlined (único residuo localhost = fallback morto do client.ts, zero IPs LAN). Gate 11/11 + mobile 35/35. **PR #11 aberto**.
- ✅ **Conta expo.dev criada pelo Boss** (projeto ID 35a02f31-baab-407a-bf93-4ddb744e7aed — pendente `eas init` linkar ao app.json). `eas init` sem token falhou como esperado (ritual: access token). NOTA: `create-expo-app` foi corrido pelo Boss p/ gerar o projeto — pasta tend/ descartável se existir; app real = apps/mobile.
- ⏳ **À espera do Boss**: (a) merge PR #11; (b) expo.dev access token → Hermes executa BG-6/7 (eas init + build Android preview p/ canário do pipeline).
- Aprendizado verificação: grep de "leak" em bundle hbc sem contexto = falso alarme; distinguir string morta (fallback ?? do código) de URL ativa antes de acusar.

## 2026-08-20 (noite) — 🎉 BG-6/7 DONE: projeto @tekton-dev/tend + PRIMEIRO BUILD NATIVO disparado; #11 merged

- ✅ **Mistério das contas expo resolvido**: o projeto 35a02f31 vivia numa **org** (não na conta pessoal). Token novo criado DENTRO da org → `whoami: tekton-dev (Developer)` → project:info: **@tekton-dev/tend** ✓. Token antigo (conta pessoal, sem acesso) → revogar (pendente Boss). Tokens: ~/.expo-token-tend2 (0600).
- ✅ **BG-6**: eas init linkado (placeholder REPLACE_ME do sisyphus substituído pelo ID real). **BG-7**: `eas build --profile preview --platform android` DISPARADO (build c86b0126) — **keystore Android criada pelo EAS**. EAS exige clean tree: 2 commits chore (briefs/omo + projectId). Build page: expo.dev/accounts/tekton-dev/projects/tend/builds/c86b0126.
- ✅ **#11 MERGED** (main c9737fa): eas.json 4 perfis + 0.1.0 + projectId. Worktree wt-plan removido, branch limpa.
- ⚠️ **Perda menor assumida**: evidence w3a-* (gitignored) vivia no worktree removido — cópia encadeada DEPOIS da remoção = perdida. Substância intacta (código/runbook no main, build no dashboard). Lição: copiar evidência ANTES de remover worktree.
- ⚠️ Stray do T1 finalmentte descartado: apps/mobile/package.json (scripts run:android/run:ios da run morta) — checkout limpo antes do pull. Se valer algo, ganha PR próprio.
- ⏳ **Build IN_QUEUE** (free tier, 90+min possível). Quando verde: APK install no Android do Boss; keystore backup ritual (EAS Credentials → 3 valores → 1Password).
- **Estado global tends**: API prod LIVE · main com W0-W3A · dogfood Expo Go pronto (Metro :8082) · build Android a cozer · iOS gated no enrollment Apple. Próximos marcos: APK verde → dogfood 2 semanas → W5 store.

## 2026-08-22 (noite) — Pack Android: o dia em que o "internal LIVE" se revelou mentira (e se consertou)

- ⛔ **Descoberta central**: o "v1.0.0 no Play internal" de 19/08 NUNCA existiu — `deploy-internal` falhava (secret SA corrompido→vazio) e `continue-on-error: true` pintava verde. Console Boss confirmou: zero AAB na app.
- ✅ **PR #16** (fix/play-upload-signal): validator de credenciais SA (JSON+campos+DER parse, `SA_INVALID`/`SA_OK`) + passo DIAG (token mint, GET tracks, serviceusage) + `continue-on-error` morto. Secret re-seeded com chave nova do Boss (`< ficheiro` byte-exact; `VAR=$(cat f)` seeda VAZIO — checklist corrigido).
- ✅ **Root cause #2**: package mismatch — app no console é **com.ramoneees.pack**, AAB era com.pack.app (DIAG: GET tracks 404 com token válido + API 200). applicationId alinhado no código (25d6c77); namespace com.pack fica; var ANDROID_PACKAGE_NAME atualizada.
- ✅ **PR #17** (agent/play-screenshots, opencode 5.3): 7 screenshots Play 1080×2160 em docs/store-assets/play/phone/ + play-screenshots.sh reproduzível + suite smoke 24 testes instrumentados (2m17s local). **Achados críticos**: (1) build internal crasha em TODA conversão vídeo/áudio — fork ffmpeg-kit 8.1.7 sem smart-exception-java; (2) CI ui-test verde a correr 0 testes (sem testInstrumentationRunner); (3) PaywallView engolia falhas billing; (4) photo picker + is_pending=1.
- ✅ **PR #18** (hotfix/ffmpegkit-crash): cherry-pick e83fca7 do #17 — fix do crash produção + runner. Merge antes do próximo release.
- ⏳ **Release v1.0.0(4) re-disparado** (run 32596908487) atrás de fila de 6 runs (1 runner só; PRs #16/#17 dispararam CI). Sobe o build com o crash de vídeo conhecido — aceitável p/ provar encanamento + dogfood de fluxos foto; (5) já nasce com #18.
- Lições: nunca transcrever chaves à mão (3× corrompi PEM; o CI é a prova); `gh secret set` lê stdin, env-var prefix é ignorado; job verde ≠ job correto (procurar continue-on-error); log de job in-progress não existe via gh — `gh run watch` ou esperar.
- Próximos passos: fila drena → confirmar upload no console (Boss) → merge #18 → release (5) → opt-in link + 12 testers (clock 14 dias) → fix i18n keys UI (achado #17) → captura mid-progress = follow-up.

Pickup: `gh run list --limit 3` + estado dos PRs #16/#17/#18.

## 2026-08-22 (fim da noite) — 🎉 PACK v1.0.0(6) DEPLOYED NO PLAY INTERNAL (desta vez é real)

- ✅ **Merges**: #16 (validator+DIAG) → #18 (FFmpegKit crash fix + runner) → #17 (screenshots+smoke) → #19 (SDK 35 + maestro package fix; CI 7/7 após rerun de flake cold-start).
- ✅ **Release v1.0.0(6) run verde 3/3** (run 32599623937): build 1m21s → upload 26s → **`Successfully committed 03358028916501970658`** — AAB no internal track, com targetSdk 35, package com.ramoneees.pack, crash fix dentro.
- Correntes da noite (todas provadas em log): secret vazio/corrompido → re-seed byte-exact; package mismatch console↔AAB → código cedeu; target 34 < mínimo 35 → bump com suppress AGP; flows maestro com appId morto → fix; 1 flake cold-start → rerun.
- **Próximo Boss**: Play Console → Internal testing → confirmar release 1.0.0(6) visível → opt-in link → instalar no Android → recrutar 12 testers (clock 14 dias). Follow-ups: retry policy maestro (flakes), fix i18n keys UI, captura mid-progress, screenshots console upload (docs/store-assets/play/phone/).
