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
