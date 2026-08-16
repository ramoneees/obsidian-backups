# Hermes SSH dedicado aos servidores (2026-08-16)

- User `hermes` criado nos nós pelo Boss; chave ed25519 do Mac em `~/.ssh/hermes_servers`.
- Aliases no `~/.ssh/config`: `olympus-server` (192.168.50.11) e `homeserver` (192.168.50.10).
- Estado: olympus-server OK (sudo NOPASSWD OK); homeserver pendente de criação do user.
- Worker nodes não têm kubectl/kubeconfig — cluster ops via kubectl do Mac ou SSH ao control-plane (homeserver).
- Configuração: useradd -m hermes, chave em authorized_keys, sudoers.d/hermes com NOPASSWD:ALL, chmod 440.

## Contexto
Criado durante o checkup do cluster (MariaDB crash loop 248x, openclaude removido, homebox fixado, jobs órfãos limpos). Primeiro uso planeado: diagnóstico do MariaDB no homeserver.
