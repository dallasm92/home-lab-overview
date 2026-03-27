# Virtualization Lab Planning Pattern

## Scope
- Source theme: choosing a practical VM lineup for a personal lab on a workstation-class hypervisor
- Purpose: document a public-safe pattern for building a compact virtualization lab that teaches the right fundamentals without overbuilding the environment too early.

## Design Goal
- Build a small virtualization lab that supports:
  - networking practice
  - Windows administration
  - Linux administration
  - basic security testing
- Keep the first wave small enough to run reliably on one main PC.

## Platform Positioning
- Desktop hypervisors such as VirtualBox are useful for:
  - learning
  - certification labs
  - proof-of-concept work
  - isolated troubleshooting
- They are not the usual production virtualization platform in enterprise environments.
- More production-like platform choices include:
  - Hyper-V
  - VMware
  - Proxmox
  - KVM-based platforms

## Starter VM Lineup
- Virtual firewall/router:
  - use a firewall VM to practice routing, NAT, DHCP, segmentation, and policy control
- Windows client VM:
  - use a workstation-style Windows VM for domain joins, policy testing, and endpoint workflows
- Linux server VM:
  - use a lightweight server VM for SSH, package management, web services, and automation practice
- Optional security target VM:
  - add an intentionally vulnerable target only when needed for isolated testing
- Optional monitoring or analysis VM:
  - add a log, IDS, or packet-analysis system only after the core network path is stable

## Sequencing Pattern
- Start with only the systems that create the lab backbone.
- Add role-specific targets after:
  - the virtual network is stable
  - addressing is predictable
  - snapshots and rollback are understood
- Avoid building too many VMs before the firewall and management path are working.

## Network Pattern
- Treat the lab as three distinct paths:
  - upstream or WAN-facing connectivity
  - management or host-access LAN
  - isolated internal lab segment
- This model supports:
  - firewall testing
  - client and server segmentation
  - safer experimentation with breakable systems

## Platform Tradeoff
- VirtualBox is often good enough for early learning and quick labs.
- Move to a more infrastructure-like platform when:
  - multi-NIC firewall behavior becomes unreliable
  - network realism matters more than convenience
  - the environment needs stronger integration with Windows or server-grade workflows

## Operational Value
- A small, role-driven VM plan produces better learning evidence than a large but unstable VM sprawl.
- The most valuable early proof points are:
  - a functioning firewall path
  - a working Windows client/server workflow
  - a repeatable Linux administration path

## Public-Safe Notes
- Keep the published version free of:
  - real internal IP ranges
  - local adapter names
  - screenshots with hostnames or credentials
