# Homelab Rebuild — Proxmox (rascunho de escopo) — 2026-08-23

**Status:** RASCUNHO — discussão arquitetural, sem data. **Trigger:** chegada do S1 Max + janela pós-lançamentos.
**Padrão:** escopo → plano (prometheus) → review adversarial → revisão → execução. Nada se executa antes do plano aprovado.

## Por que Proxmox (a tese)
1. **Backup/snapshot no hypervisor, independente do k3s** — vzdump + Proxmox Backup Server com dedup. A dor real do lab atual não é k8s, é armazenamento corrompendo em silêncio (EIO no Longhorn do homeserver, tema Ghost sumido). PBS muda a classe do RPO.
2. **Reset barato** — VM descartável e recriável em minutos; host limpo pra sempre. Alinha ao "reset-over-patch".
3. **Isolamento pra IA** — o S1 Max dedicado a VMs com GPU, sem acoplar o destino do lab ao estado de um host.
4. **Cluster de 3 nós com live-migration** — manutenção sem downtime de fim de semana.

## Estado atual (o que migra)
- homeserver (N100 16GB, control-plane) + olympus (Ryzen 5600X 64GB + RTX 2080, worker GPU)
- k3s v1.34.5 + Traefik + Longhorn + cert-manager (wildcard *.ramoneees.com) + Flux GitOps (Gitea)
- Workloads: ~130 pods (apps, databases c/ backup B2, monitoring, GPU stack vLLM/LiteLLM/n8n/openwebui, AdGuard=DNS da casa, actions-runners, sites estáticos, Ghost, Jellyfin, TubeArchivist)
- Backups atuais: rclone→B2 + restore-verify comprovado (112 tabelas gitea)

## Arquitetura alvo (proposta a validar)
| Nó | Papel |
|---|---|
| S1 Max (Strix Halo 64GB, a comprar) | Proxmox primário — VMs k3s (control-plane+worker), VM de IA local (Qwen3.8-27B) |
| olympus (Ryzen+2080) | Proxmox nó 2 — VM k3s worker GPU (passthrough RTX 2080: maduro, baixo risco) |
| homeserver (N100 16GB) | **Sai de k8s/storage.** Vira nó PBS (backup+zfs) + AdGuard dedicado. RAM não dá pra mais. |

- Flux/GitOps mantém-se: mesmos manifests, k3s renasce em VMs.
- Longhorn: decidir entre (a) manter apenas entre as 2 VMs grandes, ou (b) substituir por NFS/ZFS + replicas=1. Decisão no plano, com números.
- Rede: manter 192.168.50.x, bridges Proxmox, AdGuard inalterado pra casa (zero percebido).

## Riscos/pesquisas obrigatórias antes do plano virar execução
1. **iGPU Strix Halo passthrough no Proxmox** — ainda em maturação; spike de pesquisa obrigatório ANTES da compra decidir o formato da VM de IA. (A 2080 no Ryzen é o caminho seguro.)
2. Migração Longhorn→novo cluster = restore, não sync. Etcd/Flux/Gitea primeiro (GitOps é a chave de reconstrução — o resto renasce do Git).
3. Janela: JAMAIS durante clock de testers ativo ou baby-sleep em fase crítica. Restrição explícita no plano.

## BOSS-GATES (decisões suas)
- G-A: Confirmar compra S1 Max (€2.679) como gatilho do projeto, ou começar rebuild nos 2 nós atuais? (Recomendo: esperar o S1 — rebuild sem hardware novo = 2 migrações.)
- G-B: homeserver vira PBS+AdGuard (proposta) ou sai do lab?
- G-C: Orçamento disco novo pro nó PBS (ZFS espelhado)?
- G-D: Data-alvo — após dogfood do bebé estabilizar? Sua chamada.

## Sequência (esqueleto, plano formal depois)
1. Pesquisa: passthrough Strix Halo + PBS sizing (agentes, docs)
2. Compra S1 Max (G-A) → Proxmox bare metal nele
3. Cluster PVE 2 nós (S1 + olympus-rebuild) — olympus entra depois das VMs críticas migradas
4. k3s novo em VMs: bootstrap → Flux aponta pro MESMO repo Gitea (restaurado primeiro) → workloads renascem
5. homeserver: desativação k8s → PBS + AdGuard
6. restore-verify em TUDO (padrão B2) → decomissão do cluster velho
