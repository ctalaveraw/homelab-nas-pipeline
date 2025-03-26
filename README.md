# homelab-nas-pipeline
Homelab mono-repo deployment (soon to be hosted-on prem)

## Current infra

**Packer**:

- Create proxmox vm template, (*thin provisioned*)
  - configuration:
    - install base ubuntu + networking
    - `openssh` + key
    - `python` (for ansible connection, to config host)
    - `qemu-guest-agent` (for proxmox control of host)

**Terraform**:

- Create proxmox vm template, (*thin provisioned*)
  - configuration:
    - resuse created vm template for vm
    - add hardware configuration
    - add passthrough pcie devices

**Ansible**:

- Configure NAS (*thick provisioned*)
  - configuration:
    - connect to nas + package installation
    - user setup
    - snapraid
    - mergerfs
    - disk mounts
    - cron jobs
    - container configuration
    - reverse proxy configuration
    - network configuration

## Target infra

### Mutable infrastructure (Provisioning)

#### Tool

Ansible

#### Target hosts

- Router + OpenWRT devices
- Proxmox configuration
- Drive / HBA configuration for NAS
- NAS os config

### Immutable infrastructurer (Post-provisioning)

#### Tool

Terraform

#### Target hosts

- Docker / K8s container
