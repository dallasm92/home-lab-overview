# Internal ITSM on `pi-core`

## Objective

Document the current pattern for running an internal-only GLPI deployment on `pi-core` so the lab can support asset tracking and ticket workflow from `MAIN-PC` without increasing memory pressure on `asus-server`.

## Why `pi-core`

- `pi-core` currently has significantly more free RAM headroom than `asus-server`.
- `asus-server` is already carrying the heavier container workload in the lab.
- GLPI was treated as an internal utility application rather than a public-facing service.

## Current Deployment Shape

- Host: `pi-core`
- Platform: Docker with `docker-compose`
- App service: `glpi-app`
- Database service: `glpi-db`
- LAN access: `http://glpi.lan:8088`
- DNS target: `glpi.lan -> pi-core`

## Operational Notes

- GLPI is currently published on port `8088` because `pi-core` is already serving Pi-hole on port `80`.
- The deployment was kept minimal:
  - GLPI application
  - dedicated MySQL database
  - local backup script
- The stack is internal-only and intended for workstation access from `MAIN-PC` and other LAN clients.
- The service-catalog baseline now also exists inside GLPI:
  - pinned helpdesk/service-catalog entry: `GLPI`
  - pinned helpdesk/service-catalog entry: `Pi-hole DNS`
  - pinned helpdesk/service-catalog entry: `Homepage`
  - pinned helpdesk/service-catalog entry: `Uptime Kuma`
  - pinned helpdesk/service-catalog entry: `Immich`
  - pinned helpdesk/service-catalog entry: `Portainer`
  - all current service forms route to the `Homelab Services` category

## Data and Backup Pattern

- Deployment root: `/srv/glpi`
- Compose file: `/srv/glpi/docker-compose.yml`
- Environment file: `/srv/glpi/.env`
- Backup helper: `/srv/glpi/backup-glpi.sh`
- Off-host backup pull helper: `/home/dallas/scripts/glpi-offhost-backup-pull.sh`
- Off-host backup validator: `/home/dallas/scripts/glpi-offhost-backup-validate.sh`
- Off-host backup copy path: `/home/dallas/lab-offsite-backups/glpi`
- Docker volumes:
  - `glpi_db_data`
  - `glpi_glpi_data`

## Security Boundary

- Public documentation should not publish database passwords or root credentials from `/srv/glpi/.env`.
- GLPI should remain LAN-only unless a reverse proxy and authentication pattern are added deliberately later.
- Default GLPI installer credentials should be changed immediately after first login.

## Future Scope

- Decide later whether GLPI should stay on `:8088` or move behind an internal reverse proxy.
- Keep the service-catalog evidence in the dedicated GLPI repo unless the broader architecture overview needs a shorter summary.
