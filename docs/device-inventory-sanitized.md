# Device Inventory (Sanitized)

## Infrastructure
| Device | Role |
|---|---|
| Gateway Router | Edge routing and DHCP |
| Managed Switch | Wired aggregation and VLAN-ready switching |
| Dedicated Access Point | Wireless access |

## Compute Nodes
| Node | Role |
|---|---|
| `macmint` | Workstation and operations client |
| `asus-server` | Container host and automation engine |
| `pi-core` | DNS filtering and utility services |

## Client/Consumer Devices (Monitored)
- Streaming device
- Smart speaker class devices
- Mobile/tablet/laptop clients
- Additional unknown clients tracked for visibility until labeled

Notes:
- Public version intentionally omits MAC addresses and private addressing.
- Device labels are normalized for portfolio readability.
