# 🎓 Campus Network Design

## 📌 Project Overview
This project presents a **Campus Network Design** implemented using **Cisco Packet Tracer**.  
The network connects **Main Campus** and **Branch Campus** using **VLAN segmentation**, **Layer 3 switching**, and **Dynamic Routing (RIPv2)**.

---

## 🏗️ Network Architecture
- Main Campus (Building A, B, C)
- Branch Campus
- Cloud / WAN Network
- Layer 3 Core & Distribution Switches
- Access Layer Switches

---

## 🏫 Campus Structure

### Main Campus
- **Building A**
  - Admin
  - HR
  - Finance
  - Business
- **Building B**
  - Engineering & Computing
  - Arts & Design
- **Building C**
  - Student Labs
  - IT Department (Servers)

### Branch Campus
- Faculty of Health & Sciences
  - Staff
  - Student Labs

### External Network
- Cloud Email Server (External)

---

📐 Diagram ASCII Topologi
                           ┌──────────────┐
                           │   EMAIL /    │
                           │   WEB / FTP  │
                           │   SERVER     │
                           │ 20.0.0.2/30 │
                           └──────┬───────┘
                                  │
                            20.0.0.0/30
                                  │
                           ┌───────▼───────┐
                           │    CLOUD      │
                           │ G0/0:20.0.0.1 │
                           │ S0/1/0:10.10.10.6
                           └───────┬───────┘
                                   │
                          10.10.10.4/30
                                   │
                ┌──────────────────▼──────────────────┐
                │              MAIN-ROUTER             │
                │  G0/0 (Router-on-a-Stick)            │
                │  VLAN 10–80                           │
                │  S0/1/0:10.10.10.5                    │
                │  S0/1/1:10.10.10.1                    │
                └───────────────┬──────────────────────┘
                                │
                         TRUNK 802.1Q
                                │
                   ┌────────────▼────────────┐
                   │      MAIN-SWITCH-L3      │
                   │      (Distribution)      │
                   └─────┬─────┬─────┬───────┘
                         │     │     │
        ┌───────────────┘     │     └───────────────┐
        │                     │                     │
┌───────▼────────┐   ┌────────▼────────┐   ┌────────▼────────┐
│ SW-A-ADMIN     │   │ SW-A-HR          │   │ SW-A-FINANCE    │
│ VLAN 10        │   │ VLAN 20          │   │ VLAN 30         │
└────────────────┘   └─────────────────┘   └─────────────────┘

        ┌───────────────┐   ┌───────────────┐
        │ SW-A-BUSINESS │   │ SW-B-E&C       │
        │ VLAN 40       │   │ VLAN 50        │
        └───────────────┘   └───────────────┘

        ┌───────────────┐   ┌───────────────┐
        │ SW-B-A&D      │   │ SW-C-STUDENT  │
        │ VLAN 60       │   │ VLAN 70       │
        └───────────────┘   └───────────────┘


========================= BRANCH CAMPUS =========================

                ┌───────────────────────────────┐
                │         BRANCH-ROUTER          │
                │ G0/0 (VLAN 90,100)             │
                │ S0/2/0:10.10.10.2              │
                └───────────────┬───────────────┘
                                │
                         TRUNK 802.1Q
                                │
                     ┌──────────▼──────────┐
                     │   BRANCH-SW-L3       │
                     └───────┬───────┬─────┘
                             │       │
               ┌─────────────▼───┐ ┌─▼────────────────┐
               │ SW-BRANCH-STAFF │ │ SW-BRANCH-STUDENT │
               │ VLAN 90         │ │ VLAN 100          │
               └─────────────────┘ └──────────────────┘


## 🧱 Network Design Model
- **Core Layer**: Routers
- **Distribution Layer**: Layer 3 Switches
- **Access Layer**: Layer 2 Switches
- **Routing Protocol**: RIP Version 2 (Internal)
- **External Routing**: Static Route

---
## 🏗️ Network Architecture
- Main Campus (Building A, B, C)
- Branch Campus
- Cloud / WAN Network
- Layer 3 Core & Distribution Switches
- Access Layer Switches

---

## 🧩 VLAN & IP Addressing
Detailed VLAN and IP planning is documented in:

📄 **IP-Address-Mapping.md**  
📄 **VLAN-Port-Mapping.md**

---

## 🌐 Routing Design
- **Protocol:** RIP version 2
- **Purpose:** Enable communication between Main Campus, Branch Campus, and Cloud
- **WAN Subnets:** /30 for point-to-point efficiency

---

## 🖥️ Server Infrastructure
| Server | Location | IP |
|----|----|----|
| Web Server | IT Dept | 192.168.8.10 |
| FTP Server | IT Dept | 192.168.8.20 |
| Email Server | Cloud | 20.0.0.2 |

---

## 🧪 Network Verification
All verification steps are documented in:

📄 **VERIFICATION-CHECKLIST.md**

Includes:
- VLAN validation
- Trunk verification
- Routing table inspection
- Ping connectivity tests

---

## 🧰 Tools Used
- Cisco Packet Tracer
- Cisco IOS CLI
- Git & GitHub

---

## 📌 Author
**Eko Purwanto**  
Campus Network Design Project

---

## 📜 License
This project is licensed under the **MIT License**.
