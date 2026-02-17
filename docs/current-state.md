# Current State (Public-Safe)

Date: February 17, 2026

## Hosts
- `macmint`: workstation operations and admin tasks
- `asus-server`: Docker-based services and automation host
- `pi-core`: DNS filtering and utility services

## Service Platform
- Reverse proxy and internal DNS for standardized service endpoints
- Monitoring dashboard with HTTP and ping checks
- Backup automation with scheduled verification

## Automation
- Scheduled patch/maintenance workflows
- Scheduled backup + off-host sync + health checks
- Shared failure alert pattern for critical automation units

## Security Controls
- SSH key-based administration
- Firewall rules limited to required LAN scopes
- DNS filtering at network level
- Public documentation sanitization standards applied
