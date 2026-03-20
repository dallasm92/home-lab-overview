# Firewall Appliance Selection Notes

## Scope
- Source theme: dedicated firewall appliance evaluation from hardware inspection and role analysis
- Purpose: capture the public-safe reasoning behind choosing a fanless x86 appliance for firewall and routing duties

## Selection Pattern
- Prefer a dedicated appliance over repurposing the main server for network-edge control.
- Prioritize:
  - always-on stability
  - low power draw
  - multiple physical NICs
  - enough storage and memory for routing, VPN, logging, and moderate inspection workloads
- Treat the platform as a fixed-function network device, not as a general virtualization host.

## Why A Fanless X86 Firewall Appliance Fits
- Appliance-style hardware is well suited to:
  - edge firewall and router duties
  - VLAN gateway roles
  - DHCP and DNS-forwarding experiments
  - VPN termination
  - light-to-moderate traffic visibility and IDS/IPS testing
- The form factor is useful in a home lab because it stays quiet, can run continuously, and reinforces role separation from application hosts.

## Practical Hardware Signals
- Storage in the appliance class is often already sufficient for:
  - firewall OS
  - logs
  - backups of configuration
  - moderate monitoring or inspection data
- Mid-range memory in this class is usually enough for:
  - VLAN segmentation
  - firewall policy testing
  - VPN
  - traffic shaping
  - light IDS/IPS experimentation
- Limited expansion is acceptable when the goal is a stable network control plane rather than broad server flexibility.

## What To Confirm Before Committing
- NIC chipset support in the intended firewall OS
- port count and expected WAN/LAN or trunk layout
- storage health and replaceability
- memory ceiling
- boot behavior and whether an existing OS install is already present

## Best-Fit Use Cases
- whole-network routing and firewall policy
- trunked VLAN handoff to a managed switch
- inter-VLAN access control
- DNS enforcement or forwarding patterns
- WireGuard or IPsec lab work
- realistic firewall administration experience for portfolio and interview discussion

## Poor-Fit Use Cases
- general-purpose application hosting
- Docker or container consolidation
- heavy virtualization
- workloads that depend on broad expansion options instead of stable network I/O

## Decision Rule
- If the appliance is quiet, stable, and has supported NICs plus enough headroom for segmented routing and VPN, it is usually a better firewall platform than overloading an existing application server.

## Public-Safe Notes
- Avoid publishing:
  - teardown screenshots that expose serials, board markings, or private notes
  - exact live interface maps
  - internal addressing or hostnames tied to the current environment
