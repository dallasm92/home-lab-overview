# Pi-hole And Unbound Resolver Pattern

## Scope
- Source themes:
  - dedicated DNS utility node
  - Pi-hole local DNS
  - Unbound recursive resolution
  - DNSSEC validation
- Purpose: capture the public-safe design pattern for using Pi-hole as the client-facing resolver while Unbound handles local recursive lookups behind it.

## Design Goal
- Keep one simple DNS endpoint for clients.
- Preserve Pi-hole features:
  - ad and malware filtering
  - local DNS overrides
  - query visibility
- Move public DNS resolution behind a local recursive resolver instead of depending directly on a public upstream provider.

## Pattern
- Put Pi-hole on the DNS and utility node.
- Run Unbound on the same host, bound to loopback only.
- Point Pi-hole upstream DNS at the local Unbound listener.
- Keep clients pointed only at Pi-hole, not at Unbound directly.

Example flow:
- clients
- Pi-hole on the utility node
- Unbound on `127.0.0.1:5335`
- public DNS hierarchy

## Why This Matters
- The lab keeps one clean DNS entry point for clients and services.
- Pi-hole remains the policy layer for blocklists and local records.
- Unbound provides local recursive resolution instead of forwarding every query to one public resolver.
- DNSSEC validation happens in the recursive path, which improves trust in external answers without changing the local naming workflow.
- This makes the utility node a stronger piece of always-on core infrastructure without moving heavier application services onto it.

## Operational Model
- Local lab names continue to come from Pi-hole local DNS.
- Public names are resolved recursively by Unbound.
- Pi-hole DNSSEC validation should stay off when Unbound is doing the validation work.
- Unbound should listen on loopback only so clients cannot bypass Pi-hole policy.

## Validation Pattern
- Confirm Pi-hole upstream points at the local Unbound listener.
- Confirm Unbound is running and listening on loopback only.
- Test successful recursive lookups through Unbound.
- Test a known DNSSEC failure case and expect `SERVFAIL`.
- Reconfirm that internal local names still resolve from Pi-hole as expected.

## Public-Safe Notes
- Replace real internal IPs, local domains, and hostnames with examples before publishing.
- Do not publish private resolver inventory, full DNS zone data, or internal-only host records.
