# CasaOS On An Existing Ubuntu Server Pattern

## Overview
This pattern captures how to add CasaOS to an existing Ubuntu server that is already running other self-hosted services. The goal is to gain a lighter-weight application UI without letting a convenience layer take over core infrastructure roles that are already stable.

## When This Pattern Fits
- You already have a Linux host with Docker and a few manually managed services.
- You want a simpler UI for lower-risk applications or experiments.
- You do not want to replace existing DNS, reverse proxy, monitoring, or backup services that are already working.

## Design Choice
CasaOS fit better on the general-purpose server than on the dedicated DNS and utility node.

Reasons:
- The dedicated DNS node should stay focused on infrastructure services with minimal change.
- The general-purpose server already handled application hosting and had more room for additional service layers.
- A UI-driven platform is easier to justify on an app host than on a tightly scoped network utility node.

## Architecture Principle
- Put convenience layers on the host that is already intended for application churn.
- Keep foundational infrastructure on the host that is intended to remain quiet and predictable.
- This separates:
  - stable network services
  - operator-convenience tooling
  - lower-risk application experiments

## Integration Rules
- Keep critical infrastructure outside CasaOS when it is already stable.
- Use CasaOS as an operator convenience layer, not as the source of truth for the whole stack.
- Plan ports before installation so the UI does not collide with existing services.
- Treat Docker restarts during installation as an expected maintenance event and validate dependent services afterward.

## Why This Pattern Works
- It preserves existing operational knowledge instead of replacing it with a second control plane.
- It limits the blast radius if CasaOS needs to be removed or rebuilt later.
- It lets the operator adopt a friendlier app-management surface without moving DNS, monitoring, reverse proxy, or backup services into a less deliberate lifecycle.

## Practical Port Strategy
The clean pattern was:
- keep existing core services on their current ports
- place CasaOS on a non-conflicting alternate port
- verify listeners after installation before assuming the host is healthy

The useful lesson is not the exact port numbers. The lesson is that CasaOS can coexist with an existing stack if the port map is deliberate and checked immediately after install.

## What To Keep Outside CasaOS
- DNS and resolver services
- reverse proxy entry points
- monitoring and alerting anchors
- backup and restore automation that already has an established runbook

These services tend to matter more than the convenience gain from moving them into an app-store workflow.

## Good Candidates To Keep Inside CasaOS
- lower-risk utility apps
- dashboard-driven experiments
- services that benefit from simpler lifecycle management
- tools that are acceptable to rebuild if the platform layer changes later

## Deployment Risks To Watch
- CasaOS installation may restart or modify Docker-related services temporarily.
- Existing application listeners can be confused with CasaOS listeners if the port plan is not documented first.
- Operators can mistakenly assume a host path is usable by a container without confirming the mounted container path.
- A convenience UI can create drift if manual containers and UI-managed containers are mixed without a clear ownership rule.

## Storage And Container-Path Lesson
One of the most useful operational lessons was around storage paths for CasaOS-managed apps.

The host path is not automatically the path the container can write to. A CasaOS app only sees the paths that are actually mounted into the container. When a service fails with write or sync errors, confirm:
- the real host mount point
- the container-side path
- the runtime UID or ownership model

The practical fix is to align the application with the mounted container path instead of assuming the host filesystem layout is directly visible from inside the app.

## Ownership Rule
- Decide in advance which services are:
  - manually managed
  - reverse-proxy anchored
  - CasaOS managed
- Avoid moving an existing stable service into CasaOS just for consistency if the current runbook is already reliable.
- The cleaner pattern is to let CasaOS own only the services that genuinely benefit from its UI and lifecycle model.

## Validation Sequence
After installation or major app changes:
1. Confirm the host is still reachable.
2. Check for failed systemd units.
3. Verify Docker is healthy again.
4. Verify existing containers recovered cleanly.
5. Check the CasaOS UI path.
6. Re-test any reverse-proxied or dependent services.

## Decision Rule
- Use CasaOS when the goal is operator convenience for non-critical or rebuildable apps.
- Keep it off the dedicated DNS and utility node when that node already has a narrow, high-trust infrastructure role.
- Favor coexistence over migration unless there is a strong operational reason to consolidate more aggressively.

## Takeaway
CasaOS works well as a lightweight service-management layer on an existing Ubuntu application host when it is introduced carefully. The stable pattern is to keep foundational infrastructure where it already works, use CasaOS for lower-risk service management, and validate mount paths and recovery behavior like any other Docker-based platform layer.
