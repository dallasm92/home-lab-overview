# Monitoring and Operations

## Monitoring Coverage
- Service checks: proxy/admin/app endpoints
- Infrastructure checks: gateway, AP, switch, hosts
- Device checks: active LAN clients via ping monitoring

## Operational Workflow
1. Run validation checks across hosts and core services.
2. Verify backup timers and last successful executions.
3. Confirm DNS filtering behavior and resolver path.
4. Review monitoring status and alert health.
5. Log changes and validation results for handoff.

## Evidence Style
Each ops run records:
- Timestamp
- What changed
- What is pending
- Config paths updated (if any)

## Reliability Notes
- Consumer endpoints may appear down when sleeping.
- Critical infrastructure is monitored separately to reduce noise.
- Alert hooks are attached to high-impact scheduled tasks.
