# Home Lab Overview

Security-first home lab portfolio documenting architecture, operations, monitoring, and maintenance workflows.

Last reviewed: April 13, 2026

## What This Shows
- Multi-host Linux operations across workstation, server, and Pi infrastructure
- Centralized monitoring with service + device health checks
- Automated maintenance, backup, and failure-alert workflows
- Public-safe documentation style (no real internal IPs, credentials, or secrets)

## Environment Summary (Sanitized)
- `macmint` (Linux Mint workstation)
- `asus-server` (Ubuntu Server + Docker services)
- `pi-core` (Pi-hole DNS + utility services)
- Managed switch + dedicated access point + gateway router

## Current Operations Snapshot
- Internal service routing standardized through `*.lan`
- Uptime monitoring for services and LAN devices
- Scheduled backup and healthcheck jobs with failure alert hooks
- Daily malware-signature updates + scheduled on-demand scans

## Best Use In Portfolio Review
Use this repo to show:
- architecture thinking
- monitoring and operations maturity
- public-safe documentation standards

For direct troubleshooting evidence, start with:
- [IT Support Labs](https://github.com/dallasm92/it-support-labs)
- [Active Directory Lab](https://github.com/dallasm92/ad-lab-windows-server-2022)
- [PC Build - MAIN-PC](https://github.com/dallasm92/pc-build-main-pc)

See:
- `docs/current-state.md`
- `docs/device-inventory-sanitized.md`
- `docs/monitoring-and-operations.md`
- `docs/public-sanitization-standard.md`
- `docs/firewall-platform-and-vlan-plan.md`
- `docs/unified-dashboard-and-monitoring-pattern.md`
- `docs/switch-operations-and-hardening.md`
- `docs/dns-and-local-naming-pattern.md`
- `docs/pihole-unbound-resolver-pattern.md`
- `docs/equipment-and-role-model.md`
- `docs/standalone-ap-management-pattern.md`
- `docs/server-installation-observations.md`
- `docs/firewall-appliance-selection-notes.md`
- `docs/virtual-firewall-vlan-lab-pattern.md`
- `docs/virtualization-lab-planning-pattern.md`
- `docs/repurposed-pc-to-ubuntu-server-pattern.md`
- `docs/headless-dns-utility-node-pattern.md`
- `docs/internal-itsm-on-pi-core-pattern.md`
- `docs/isp-router-to-dedicated-firewall-transition-pattern.md`
- `docs/casaos-on-existing-ubuntu-server-pattern.md`

## Core Repositories
- AI-Assisted Home Lab Operations:
  - https://github.com/dallasm92/ai-assisted-home-lab-operations
- Lab Maintenance (Ansible):
  - https://github.com/dallasm92/lab-maintenance
- IT Support Labs:
  - https://github.com/dallasm92/it-support-labs

## Security Posture for Public Repos
- No real private addressing in public docs/examples
- No credentials, API tokens, secrets, or private keys
- No internal backup paths, mount points, or host fingerprints
- Sanitized host aliases and representative architecture only

See `SECURITY.md` for full publication standards.
