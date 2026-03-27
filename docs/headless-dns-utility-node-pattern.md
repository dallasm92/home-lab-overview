# Headless DNS Utility Node Pattern

## Scope
- Source themes:
  - Pi-hole as a dedicated internal resolver
  - low-power headless host role design
  - pointing infrastructure hosts at the intended local DNS service
- Purpose: capture the public-safe pattern for using a small always-on node as a DNS anchor and lightweight utility-services platform.

## Role Definition
- Use a low-power headless system as a stable utility node for:
  - internal DNS
  - local naming
  - lightweight monitoring or dashboard services
  - small operational helpers that benefit from being isolated from the main application server
- Treat the node as infrastructure support, not as a general-purpose workload target.

## Why This Pattern Works
- DNS is operationally safer when it lives on an always-on system with a narrow role.
- A headless utility node gives the lab:
  - predictable name resolution
  - lower power and noise than a full server
  - cleaner role separation between infrastructure services and application hosting
  - a practical platform for service-health dashboards or simple monitoring tools

## Service Placement Pattern
- Keep the resolver role primary.
- Add only lightweight secondary services that support operations, such as:
  - dashboard views
  - uptime checks
  - simple host telemetry
- Avoid piling on unrelated application workloads that could compete with DNS stability.

## Client Configuration Pattern
- Point infrastructure hosts at the utility node as their primary resolver.
- Prefer explicit resolver configuration over relying on public DNS fallbacks.
- Add local records or equivalent local-name support for key infrastructure systems before standardizing on friendly names.

## Validation Pattern
- Confirm clients can query the resolver directly.
- Verify the host is actually using the intended resolver after configuration changes.
- Test both:
  - general internet name resolution
  - internal service and host lookups
- Recheck resolution from more than one node before treating the naming layer as production-ready.

## Operational Notes
- Keep the DNS node easy to rebuild and document.
- Use conservative service exposure and avoid publishing sensitive UI captures, admin tokens, or internal addressing.
- If multiple dashboard or monitoring tools are added, keep them on non-conflicting ports and treat them as secondary to DNS availability.

## Decision Rule
- If a small always-on node can provide stable DNS plus a few lightweight operator services, it is usually a better fit for that role than mixing DNS into a busier application server.
