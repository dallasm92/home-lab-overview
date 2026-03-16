# Switch Operations And Hardening

## Scope
- Source themes:
  - managed switch bring-up
  - security baseline for a small lab switch
- Purpose: document the public-safe baseline for bringing a managed switch online and hardening it for a homelab.

## Primary Role
- Central Ethernet aggregation point for the lab
- Foundation for:
  - future VLAN segmentation
  - AP uplinks
  - firewall integration
  - link and port visibility

## Bring-Up Sequence
1. Power on and connect an uplink plus one management workstation.
2. Discover the switch management IP.
3. Log in and change the default administrative password.
4. Assign a stable management IP or reservation.
5. Update firmware before making more complex changes.
6. Label ports to match actual device roles.
7. Back up the running configuration.

## Baseline Hardening Pattern
- Enable encrypted management where available.
- Disable legacy or unnecessary management paths where practical.
- Disable unused ports or place them into an isolated network.
- Disable PoE on ports that do not need it.
- Enable loop detection and storm-control style safeguards.
- Enable IGMP snooping for cleaner multicast behavior.

## Segmentation Pattern
- Avoid leaving the full lab on the default switch VLAN forever.
- Create a primary operational VLAN for active devices.
- Use a separate quarantine or dead-end VLAN for unused ports.
- Keep changes staged and reversible to avoid management lockout.

## Public-Safe Notes
- Do not publish:
  - real switch management IPs
  - real port-to-device maps
  - screenshots with actual VLAN names tied to the live environment unless reviewed
