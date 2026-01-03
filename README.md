# home-lab-overview



🧪 Home Lab Overview

Purpose



This repository provides a high-level overview of my personal home lab environment.

The lab is designed to mirror real-world IT and small-business infrastructure and is used to build hands-on experience in:



Networking fundamentals



Virtualization



Linux and Windows Server administration



DNS and basic security concepts



Professional documentation and troubleshooting



This repo serves as the architecture and navigation hub for my other lab repositories.



🖥️ Core Devices \& Roles (Sanitized)

Windows 11 Desktop (Hyper-V Host)



Role: Primary workstation and virtualization host



OS: Windows 11 Pro



Virtualization: Hyper-V



Storage:



NVMe 1 TB



NVMe 500 GB



Virtual Machines



Windows Server



Kali Linux



Ubuntu



RHEL 9 (Lab)



Linux Mint



Elementary OS



Used for Windows Server labs, Linux administration, security testing, and multi-OS interoperability.



Ubuntu Server (Always-On Server)



OS: Ubuntu Server



Connection: Ethernet



Role:



Docker host



Linux server administration



Long-running services



DNS services are intentionally separated and handled by a dedicated Raspberry Pi.



Raspberry Pi 5 (DNS \& Core Services)



Role: Centralized DNS filtering (Pi-hole)



Connection: Ethernet



Storage: NVMe



Operation: Headless



Used to centralize DNS, test networking behavior, and host lightweight infrastructure services.



🌐 Networking Equipment

ISP-Provided Hardware



Modem: Spectrum (ISP-provided)



Router: Spectrum (ISP-provided)



NAT



DHCP



Wi-Fi access point



Managed Switch



Model: Netgear GS308EP



Layer: 2 (VLAN-capable)



Purpose: Central wired connectivity and future segmentation



Switch Port Map



Port	Device

1	Router

2	Windows 11 Desktop

3	Ubuntu Server

4	Raspberry Pi 5

📡 Wireless Clients



Connected via router Wi-Fi:



Amazon Alexa Dot



Apple TV



Xumo Box (Fire TV)



iPhones (2)



HP Victus Laptop



MacBook (Linux Mint)



Kindle



iPad



Epson XP-4200 Printer (Wi-Fi capable)



The printer is currently USB-connected to the desktop, with planned migration to full network printing.



🧩 Physical Network Diagram

&nbsp;                     Internet

&nbsp;                         │

&nbsp;                 \[ Spectrum Modem ]

&nbsp;                         │

&nbsp;                 \[ Spectrum Router ]

&nbsp;                 (NAT • DHCP • Wi-Fi)

&nbsp;                         │

&nbsp;                 ────────┴────────

&nbsp;                         │

&nbsp;       \[ Netgear GS308EP Managed Switch ]

&nbsp;                         │

&nbsp;       ┌───────────────┬───────────────┬───────────────┐

&nbsp;       │               │               │

&nbsp;\[Windows 11 PC]   \[Ubuntu Server]   \[Raspberry Pi 5]

&nbsp;Hyper-V Host       Docker / Services   DNS (Pi-hole)



🧠 Logical Network Diagram

&nbsp;                        Internet

&nbsp;                            │

&nbsp;                  ┌─────────▼─────────┐

&nbsp;                  │ Spectrum Router     │

&nbsp;                  │ NAT • DHCP • Wi-Fi  │

&nbsp;                  └─────────┬─────────┘

&nbsp;                            │

&nbsp;            ┌───────────────▼───────────────┐

&nbsp;            │ Netgear GS308EP (Layer 2)       │

&nbsp;            └───────────────┬───────────────┘

&nbsp;                            │

&nbsp;       ┌───────────────┬───────────────┬───────────────┐

&nbsp;       │               │               │

┌───────▼───────┐ ┌─────▼────────┐ ┌─────▼────────┐

│ Windows 11 PC │ │ Ubuntu Server│ │ Raspberry Pi │

│ Hyper-V Host  │ │ Docker Host  │ │ DNS (Pi-hole)│

│ Multiple VMs  │ │              │ │              │

└───────────────┘ └──────────────┘ └──────────────┘



🔍 DNS Flow

Client Devices

&nbsp;     │

&nbsp;     ▼

&nbsp;Raspberry Pi (Pi-hole)

&nbsp;     │

&nbsp;     ▼

&nbsp;Upstream DNS (ISP / Public)

&nbsp;     │

&nbsp;     ▼

&nbsp;  Internet





All wired and wireless clients use centralized DNS filtering.



🎯 Design Principles



Separation of concerns



Centralized DNS



Dedicated virtualization host



Managed switching



Minimal complexity with clear learning value



Security-conscious public documentation



📂 Related Repositories (Learning Progression)



IT Support Labs

Ticket-style troubleshooting labs

https://github.com/dallasm92/it-support-labs



PC Build – Windows 11 Desktop (planned)

Hardware research, build process, and validation



Hyper-V Virtualization Lab (planned)

Multi-OS virtualization and Windows Server labs



Linux Server Services (planned)

Ubuntu Server administration and Docker services



DNS \& Pi-hole Lab (planned)

DNS filtering, testing, and troubleshooting



🚀 Future Improvements



Convert printer to full network printing



VLAN design and documentation



Dedicated firewall appliance



Monitoring and uptime tracking



Expanded service documentation



📌 Why This Lab Exists



This lab exists to build and demonstrate practical, real-world IT skills through hands-on experimentation, troubleshooting, and documentation, while maintaining a clean and security-conscious public portfolio.

