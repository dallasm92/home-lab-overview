# Standalone AP Management Pattern

## Scope
- Source theme: LAN-only management of a standalone access point
- Purpose: document the public-safe pattern for local wireless management without cloud dependency.

## Design Goal
- Keep wireless management local to the network.
- Avoid unnecessary cloud accounts for a single-device or early-stage AP deployment.

## Pattern
- Use standalone management mode when:
  - there is only one AP
  - a full controller is not yet needed
  - cloud dependency is undesirable
- Configure:
  - local administrator credentials
  - SSID and security
  - firmware review
  - stable local management addressing

## Why This Matters
- It aligns with a privacy-conscious and LAN-first operations style.
- It keeps the AP useful immediately while leaving room to adopt a controller later if the environment grows.

## Growth Path
- Start with standalone mode for one device.
- Move to controller-based management later if you add:
  - multiple APs
  - more switches
  - site-wide policy needs

## Public-Safe Notes
- Do not publish:
  - real SSIDs
  - real AP IPs
  - screenshots containing wireless keys or client lists
