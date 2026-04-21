# Hyper-V Workstation Lab Foundation Pattern

## Scope
- Source theme: using Hyper-V on a Windows workstation as the starting point for a structured personal lab
- Purpose: capture a public-safe pattern for turning a Windows workstation into a practical lab host with a predictable switch layout and a first-pass firewall-backed VM path.

## Design Goal
- Use Hyper-V as a workstation hypervisor for:
  - Windows and Linux lab VMs
  - firewall and segmentation experiments
  - domain and endpoint workflow practice
- Keep the first build small enough to troubleshoot before adding more systems.

## Foundation Pattern
- Confirm virtualization support and Windows edition before enabling Hyper-V.
- Set default storage paths early so VM configs, disks, and ISO media stay organized.
- Start with two distinct virtual switch roles:
  - an external switch for upstream LAN or internet access
  - an internal switch for isolated lab traffic
- Build the network backbone first, then place guests behind it.

## Recommended First Layout
- Workstation host:
  - Hyper-V management
  - local admin and console access
- External virtual switch:
  - upstream connectivity for WAN-facing or bridged VM traffic
- Internal virtual switch:
  - isolated lab segment for breakable systems and staged services
- First backbone VM:
  - a virtual firewall or router with one NIC on each switch
- Early guest VMs:
  - one Linux server or utility VM
  - one Windows client VM when endpoint or domain practice is needed

## Hyper-V Networking Notes
- External switch creation can be disrupted by other virtualization or VPN adapters.
- When switch creation fails, check:
  - Hyper-V service health
  - physical NIC binding for the Hyper-V switch component
  - competing host-only, VPN, or other virtual adapters
- The built-in Default Switch is convenient for quick access, but it is not the best fit when you want predictable addressing and topology.

## First Firewall VM Pattern
- Attach WAN to the external switch.
- Attach LAN to the internal switch.
- Use a lab subnet that does not overlap the real home subnet.
- Enable DHCP on the lab LAN only after the interface plan is clear.
- Validate host access to the firewall before adding more guests behind it.

## Practical Compatibility Notes
- Hyper-V can coexist with VirtualBox, but adapter conflicts and performance tradeoffs still matter.
- FreeBSD-derived firewall appliances may require:
  - Secure Boot disabled on Generation 2
  - a simpler filesystem choice if the first boot path proves unstable
- If the first boot path is unreliable, reduce variables before rebuilding:
  - simplify the VM generation choice
  - simplify the storage format
  - re-check boot order and attached install media

## Operational Value
- This pattern creates a strong foundation for:
  - firewall labs
  - Windows client and server testing
  - Linux administration practice
  - future VLAN and segmentation work
- It also produces clearer documentation evidence than creating several unrelated VMs without a network plan.

## Public-Safe Notes
- Replace local adapter labels, private paths, and exact subnets with examples before publishing screenshots.
- Avoid publishing screenshots that reveal hostnames, local usernames, or full workstation inventory details.
