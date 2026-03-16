# Equipment And Role Model

## Scope
- Source theme: current homelab devices and their intended roles
- Purpose: summarize the public-safe role assignment of the major lab devices without exposing private inventory detail.

## Core Roles
- Primary workstation:
  - documentation
  - virtualization
  - day-to-day administration
- Primary server:
  - always-on service host
  - container platform
  - automation and maintenance execution
- Utility node:
  - DNS and lightweight support services
  - small always-on infrastructure tasks
- Admin laptop or secondary workstation:
  - Linux-based administration
  - SSH access
  - scripting and repo work

## Network Roles
- Managed switch for wired aggregation and segmentation growth
- Consumer gateway or upstream router for internet edge access
- Dedicated firewall path planned or adopted for more realistic network control
- Optional AP layer for wireless integration

## Why This Structure Works
- It separates responsibilities across hosts instead of forcing one machine to do everything.
- It supports progressive growth:
  - start simple
  - add segmentation
  - add service standardization
  - add monitoring and automation

## Public-Safe Notes
- Prefer host roles over exact personal hardware identifiers in public documentation.
