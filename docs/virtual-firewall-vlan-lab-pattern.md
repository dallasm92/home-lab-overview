# Virtual Firewall VLAN Lab Pattern

## Scope
- Source theme: first-pass VLAN segmentation lab using a virtualized firewall plus a managed switch
- Purpose: capture the public-safe design pattern for learning VLANs, DHCP scopes, and inter-VLAN policy without turning the note into a UI-specific walkthrough

## Lab Goal
- Use a firewall platform as the routing point for multiple VLANs.
- Pair it with a managed switch so each segment has:
  - its own subnet
  - its own DHCP scope
  - default isolation from the other segments

## Recommended Segment Pattern
- Admin or primary user network
- Server network
- Guest or IoT network
- Optional quarantine or restricted network

## Core Design Rule
- Keep one uplink between the firewall LAN side and the switch as the multi-VLAN handoff.
- Treat end-device ports as single-purpose access ports unless a host explicitly needs trunked networks.
- Keep a safe management path available while staging VLAN changes so the switch can still be reached if the lab design is incomplete.

## Virtual Firewall Considerations
- A virtualized firewall can still teach the right concepts:
  - interface assignment
  - VLAN creation
  - DHCP scope design
  - firewall rule direction
  - inter-VLAN policy
- The main risk is operational complexity:
  - the host running the firewall may also be one of the devices affected by the network changes
  - trunk and access-port changes can interrupt both administration and connectivity if applied too early

## Safe Build Sequence
1. Define VLAN IDs and roles before changing live ports.
2. Keep the default or management VLAN available until the new design is proven.
3. Create VLAN interfaces on the firewall side first or stage them alongside switch changes.
4. Assign one subnet and DHCP range per VLAN.
5. Apply switch access-port changes gradually, starting with non-critical ports.
6. Test DHCP, gateway reachability, and internet access one VLAN at a time.
7. Leave inter-VLAN traffic blocked by default, then add only the minimum required allow rules.

## Useful Validation Checks
- each client lands in the expected subnet
- the firewall presents the correct default gateway per segment
- DHCP ranges do not overlap
- switch management remains reachable
- server access is only available from the intended admin segment
- guest or test segments reach the internet without broad access to internal hosts

## Main Lessons
- Segmentation work is easier to manage when the switching plan and firewall-interface plan are treated as one change set.
- Virtual firewalls are good for learning, but they require extra attention to host uplinks and recovery paths.
- A quarantine VLAN is useful as both a security control and a safety valve for unused or untrusted ports.

## Public-Safe Notes
- Avoid publishing:
  - real live port numbers tied to actual devices
  - exact internal subnets from the home network
  - screenshots of switch or firewall UI unless they have been manually reviewed
