# Repurposed PC To Ubuntu Server Pattern

## Scope
- Source theme: converting an older personal desktop into a simple Ubuntu Server host
- Purpose: document a public-safe pattern for reusing consumer hardware as a practical Linux backup server instead of treating it as retired e-waste.

## Design Goal
- Extend the useful life of older hardware.
- Move the system from casual desktop use into a stable infrastructure role.
- Give the server one clear first job:
  - accept backups and file transfers from a primary workstation

## Migration Pattern
- Retire the previous desktop operating system.
- Create boot media with a straightforward imaging tool and a USB installer.
- Install a server-focused Linux distribution instead of another desktop OS.
- Keep the first deployment simple:
  - remote administration
  - backup target role
  - basic network service validation

## Documentation Pattern
- If original install screenshots are unavailable, use current-state evidence instead.
- Capture:
  - operating system version
  - host identity
  - remote access status
  - firewall posture
  - listening services
  - storage or share role
- Treat the writeup as a post-build audit rather than a reconstruction of every installer screen.

## First Practical Role
- Use the repurposed server as a backup and file-share target for a main workstation.
- Keep the role narrow at first:
  - backup destination
  - SSH administration
  - optional lightweight self-hosted services
- Expand only after the baseline is stable and documented.

## Why This Has Portfolio Value
- It shows:
  - hardware repurposing
  - Linux server adoption
  - practical operations thinking
  - evidence-based documentation
- It is stronger than a generic install walkthrough because the server has a real operational job.

## Public-Safe Notes
- Replace internal IPs, usernames, and share names with generic examples.
- Focus on current validated behavior rather than perfect installation chronology.
