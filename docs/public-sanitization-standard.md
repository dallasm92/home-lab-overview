# Public Sanitization Standard

This project uses strict publication controls.

## Never Publish
- Real private IPv4/IPv6 addressing
- Credentials, secrets, API keys, private keys
- Internal backup targets and mount topology
- Host key material or trust fingerprints

## Allowed
- Sanitized host aliases (`macmint`, `pi-core`, etc.)
- Representative DNS suffixes (`*.lan`)
- Redacted workflows and architecture patterns
- Example/test-only addressing (`192.0.2.0/24`, `198.51.100.0/24`, `203.0.113.0/24`)

## Pre-Publish Checklist
- Search for private addressing patterns
- Search for key/secret/token patterns
- Verify screenshots do not expose sensitive identifiers
