# Firewall Platform And VLAN Plan

## Scope
- Source themes:
  - dedicated firewall appliance evaluation
  - first-pass VLAN segmentation design
- Purpose: capture the public-safe design intent behind the firewall platform and the initial VLAN plan.

## Hardware Role
- Dedicated fanless x86 firewall appliance
- Intended role:
  - edge firewall and router
  - VLAN gateway
  - DHCP / DNS-forwarding / VPN learning platform
- Operational design goal:
  - keep firewall duties isolated from general application hosting

## Platform Assessment
- The firewall platform was treated as a fixed-function network device rather than a general server.
- Major conclusions:
  - enough storage for typical firewall workloads
  - enough memory for routing, VLANs, VPN, IDS/IPS experiments, and traffic visibility
  - appliance-style hardware is appropriate for always-on network control
  - limited expansion reinforces using it only for network control services

## Intended Learning Outcomes
- Practical experience with:
  - routing and firewall policy
  - VLAN segmentation
  - DHCP scopes
  - inter-VLAN access control
  - VPN concepts
  - network observability
- Resume-safe networking evidence without exposing private infrastructure details

## Initial VLAN Design Pattern
- Management / admin network
- Server network
- Guest or isolated test network
- Optional quarantine or restricted network

## Switching Pattern
- Firewall LAN uplink acts as the trunk for multiple tagged VLANs.
- End-device switch ports act as access ports for one VLAN at a time.
- Default switch VLAN remains available for management compatibility when needed.

## Firewall Policy Pattern
- Start with isolation by default between VLANs.
- Add explicit allow rules only where a clear operational need exists.
- Use the admin VLAN as the only network with broad management access.

## Public-Safe Notes
- Avoid publishing:
  - exact switch port maps tied to the live environment
  - real hostnames or internal DNS names
  - exact internal IP addressing
  - screenshots until they are reviewed for UI labels and addresses
