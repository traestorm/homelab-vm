# Homelab VMs & Containers

Virtualization layer. Depends on [homelab-network](https://github.com/traestorm/homelab-network)
being operational.

## Architecture

| Layer | Tech | Notes |
|---|---|---|
| Hypervisor | Proxmox | |
| Containers | Docker / Podman | |
| Orchestration | kind (K8s in Docker) | Local 3-node cluster |
| Provisioning | Ansible | |
| IaC | Terraform | |

## Quick Start

```bash
# Create a new VM from base image
./vm/scripts/create-vm.sh web-server 4 8192 50

# Start the container stack
cd containers/docker-compose && cp .env.example .env && docker compose up -d

# Start the K8s cluster
cd containers/k8s && kind create cluster --config kind-config.yaml
```

## VM Inventory

| VM | Purpose | Resources | Status |
|---|---|---|---|
| web-server | Test web apps | 4 vCPU / 8 GB / 50 GB | ⬜ |
| database | PostgreSQL, MySQL | 4 vCPU / 16 GB / 100 GB | ⬜ |
| k8s-worker | K8s worker nodes | 8 vCPU / 16 GB / 100 GB | ⬜ |

## Not committed

- VM disk images (too large)
- Ansible vault password
- Terraform state
- Container secrets / .env
```
