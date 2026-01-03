# 🧪 Home Lab Overview

## Start Here
- 🧭 Portfolio hub (this repo): architecture + navigation
- 🧰 Ticket-style troubleshooting: https://github.com/dallasm92/it-support-labs
- 🖥️ PC build + validation: https://github.com/dallasm92/pc-build-main-pc

**One-line lab summary:** Windows 11 Hyper-V host + always-on Ubuntu Server (Docker/services) + Raspberry Pi 5 (Pi-hole DNS) + managed Layer-2 switch + ISP router (NAT/DHCP/Wi-Fi).

---

## Purpose
This repository provides a **high-level overview** of my personal home lab environment.  
It mirrors real-world IT / small-business infrastructure and helps me build hands-on experience in:

- Networking fundamentals
- Virtualization
- Linux and Windows Server administration
- DNS and basic security concepts
- Professional documentation and troubleshooting

This repo is the **architecture + navigation hub** for my other lab projects.

---

## 🧠 Architecture Summary
- Dedicated Windows 11 desktop for virtualization (Hyper-V)
- Separate always-on Ubuntu Server for services
- Raspberry Pi dedicated to DNS filtering (Pi-hole)
- Managed switch for wired connectivity
- ISP router handling NAT, DHCP, and Wi-Fi
- Mixed wired + wireless client environment

**Design focus**
- Separation of concerns
- Minimal complexity (while still realistic)
- Repeatable IT workflows
- Security-conscious public documentation

---

## 🖥️ Core Devices & Roles (Sanitized)

| Device | Role |
|------|-----|
| Windows 11 Desktop | Hyper-V host, primary workstation |
| Ubuntu Server | Docker host, always-on services |
| Raspberry Pi 5 | Centralized DNS filtering (Pi-hole) |
| Netgear GS308EP | Managed Layer-2 switch |
| ISP Router | NAT, DHCP, Wi-Fi access point |

---

## 🌐 Network Overview
- Wired devices connect through the managed switch
- Wireless devices connect through the ISP router
- All clients use centralized DNS filtering

### DNS Flow (Simplified)
Client → Pi-hole (Raspberry Pi) → Upstream DNS (ISP/Public) → Internet

---

## 🧩 Physical Topology (Simplified)

<details>
<summary>Click to expand physical network diagram</summary>

Internet
|
[Spectrum Modem]
|
[Spectrum Router]
(NAT • DHCP • Wi-Fi)
|
[Netgear GS308EP Switch]
├── Windows 11 Desktop (Hyper-V)
├── Ubuntu Server (Docker)
└── Raspberry Pi 5 (DNS / Pi-hole)

</details>

---

## 📡 Wireless Clients (Examples)
- Amazon Alexa Dot
- Apple TV
- Xumo Box (Fire TV)
- iPhones (2)
- HP Victus Laptop
- MacBook (Linux Mint)
- Kindle
- iPad
- Epson XP-4200 Printer

---

## 📂 Related Repositories (Learning Progression)

| Stage | Repository | Focus |
|----|-----------|------|
| 1 | [IT Support Labs](https://github.com/dallasm92/it-support-labs) | Ticket-style troubleshooting |
| 2 | [PC Build – Main PC](https://github.com/dallasm92/pc-build-main-pc) | Hardware research, build, and validation |
| 3 | Hyper-V Virtualization Lab *(planned)* | Multi-OS + Windows Server labs |
| 4 | Linux Server Services *(planned)* | Ubuntu Server + Docker |
| 5 | DNS & Pi-hole Lab *(planned)* | DNS filtering + testing |

---

## 🚀 Future Improvements
- Convert printer to full network printing
- VLAN design and documentation
- Dedicated firewall appliance
- Monitoring and uptime tracking
- Expanded service documentation

---

## 🔒 Sanitization & Security
This public repo intentionally omits sensitive details (exact IPs, hostnames, keys, internal configs).  
Documentation focuses on architecture, workflows, and troubleshooting methodology.

_Last updated: 2026-01-03_

---

## 📌 Why This Lab Exists
This lab exists to build and demonstrate practical, real-world IT skills through hands-on experimentation, troubleshooting, and documentation — while maintaining a clean, professional, and security-conscious public portfolio.

