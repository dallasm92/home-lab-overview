# DNS And Local Naming Pattern

## Scope
- Source themes:
  - local DNS records
  - hosts pointing at the intended resolver
- Purpose: capture the public-safe operational pattern for making internal service names consistent and pointing hosts at the correct DNS resolver.

## Design Goal
- Use a dedicated internal DNS service as the resolver for always-on hosts and internal services.
- Replace raw IP-based access with friendly local names.
- Support dashboards, monitoring, and routine administration with predictable internal addressing.

## Pattern
- Pick one resolver as the primary local DNS authority.
- Point infrastructure hosts at that resolver.
- Add local DNS records or equivalent local-name support for key systems and services.
- Validate resolution from clients and servers before relying on names operationally.

## Why This Matters
- Friendly names reduce operational friction.
- Internal service naming improves:
  - dashboards
  - monitoring targets
  - SSH and RDP habits
  - future reverse-proxy routing
- DNS standardization also makes migration and service relocation easier later.

## Validation Pattern
- Test direct resolver queries.
- Confirm the host uses the intended resolver instead of a public fallback.
- Test both:
  - public DNS lookups
  - local service or host lookups

## Public-Safe Notes
- Replace real internal domains, hostnames, and IPs with examples before publishing.
