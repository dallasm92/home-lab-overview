# ISP Router To Dedicated Firewall Transition Pattern

## Scope
- Source theme: deciding when to keep an ISP router in place versus introducing a dedicated firewall appliance
- Purpose: document a public-safe pattern for moving from a consumer gateway to a more intentional firewall design without destabilizing the home network too early.

## Design Goal
- Improve network control and learning value without causing an unnecessary whole-network outage.
- Use a staged transition instead of swapping the edge architecture all at once.

## Core Tradeoff
- The ISP router usually offers low-friction stability.
- The dedicated firewall offers better visibility, segmentation, policy control, and learning value.
- The transition problem is not which device is "better" in theory. The real problem is how to gain the firewall benefits without turning the home network into an outage lab.

## Two Valid Operating Models

### 1. ISP Router Stays In Front
- The ISP router remains the primary internet gateway.
- The dedicated firewall is introduced behind it for:
  - a lab segment
  - firewall training
  - VLAN experiments
  - controlled migration work
- This is the safer first step when the new firewall is still being configured.

### 2. Dedicated Firewall Becomes The Primary Gateway
- The dedicated firewall takes over routing and policy enforcement for the network behind it.
- The ISP router is reduced to:
  - upstream handoff
  - modem-adjacent gateway role
  - or removed entirely when the ISP connection allows it
- This model provides the strongest learning value, but only after staging and validation are complete.

## Why Start Behind The Existing Router
- It reduces blast radius.
- It preserves normal internet access for the rest of the household while the new firewall is still being tested.
- It lets the operator validate:
  - interface mapping
  - DHCP behavior
  - DNS behavior
  - client reachability
  - policy changes
without taking over the whole environment on day one.

## Validation Goals In The Staging Phase
- Confirm the firewall can act as a dependable router for at least one controlled segment.
- Validate:
  - interface mapping accuracy
  - NAT and outbound reachability
  - DHCP scope behavior
  - DNS forwarding or resolver behavior
  - management access after reboots or config changes
- This creates evidence that the firewall is ready for broader responsibility instead of relying on a one-time successful setup.

## Staging Pattern
- Start with an isolated management or lab path:
  - one test client
  - one dedicated firewall LAN segment
  - no dependency from the rest of the house on the new device yet
- Confirm:
  - management access
  - expected addressing
  - DNS and gateway behavior
  - stable WAN handoff from the upstream router

## Promote-To-Primary Checklist
- Before promoting the dedicated firewall, confirm:
  - documented interface roles
  - known-good management access path
  - intentional DHCP ownership
  - intentional DNS ownership
  - switch uplink and VLAN plan
  - rollback path if the migration fails
- The migration should be a controlled cutover, not an exploratory live test.

## Transition Trigger
- Move from "behind the ISP router" to "primary gateway" only when:
  - interface roles are confirmed
  - management access is reliable
  - DHCP and DNS scope decisions are intentional
  - the switch uplink plan is clear
  - rollback is understood

## Common Mistakes
- Replacing the edge router before management access is dependable.
- Changing gateway, DHCP, and DNS ownership at the same time without a rollback plan.
- Treating a successful first boot as the same thing as an operationally validated firewall.
- Designing the final topology before proving that the staged lab segment is stable.

## Decision Rule
- If the goal is safe learning and low household disruption, keep the ISP router in front first.
- If the goal is realistic edge-firewall ownership and the new firewall has already been validated, promote the dedicated firewall to the primary gateway.

## Portfolio Value
- This pattern shows:
  - staged migration thinking
  - outage-risk reduction
  - realistic network change management
  - understanding of the difference between a lab firewall and a production gateway role

## Public-Safe Notes
- Avoid publishing:
  - live WAN details
  - real ISP account or modem information
  - exact interface maps tied to the current environment
  - screenshots with internal addressing or service labels
