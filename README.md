# Cisco Packet Tracer Projects

## Overview

This repository contains a collection of **network design, simulation, and troubleshooting projects** developed using **Cisco Packet Tracer**.  
The projects demonstrate **CCNA-level technical competencies** and reflect **real-world enterprise networking and NOC operational scenarios**.

All implementations follow **industry best practices**, focusing on structured network architecture, segmentation, routing, verification, and incident handling.

This portfolio is suitable for:
- CCNA practice and preparation
- Network Operations Center (NOC) roles
- Junior Network Engineer positions
- IT Support (Networking-focused)
- Academic and professional reference

---

## Professional Summary

Networking enthusiast with hands-on experience in designing, configuring, and troubleshooting enterprise networks using Cisco Packet Tracer.  
Strong foundation in VLAN segmentation, IP addressing, routing, and Cisco IOS CLI.  
Actively building a professional portfolio aligned with CCNA certification and NOC operational standards.

---

## Skills Demonstrated

### Networking Skills
- Network topology design (LAN, Campus, Enterprise, Branch)
- IP Addressing and Subnetting (IPv4)
- VLAN creation and segmentation
- Inter-VLAN Routing
- Static and basic dynamic routing
- Cisco Router and Switch configuration (IOS CLI)
- End-to-end connectivity testing and verification

### NOC & Operational Skills
- Network incident analysis and troubleshooting
- Root Cause Analysis (RCA)
- Layer 1–3 fault isolation
- Incident documentation and validation
- L1 to L2 escalation awareness

### Tools & Technologies
- Cisco Packet Tracer
- Cisco IOS Command Line Interface (CLI)
- Network simulation and troubleshooting

### Professional Skills
- Structured and hierarchical network design
- Technical documentation
- Analytical problem-solving
- Attention to detail
- ITIL-aligned incident handling mindset

---

## Repository Structure

Each directory represents a standalone network simulation project and contains Cisco Packet Tracer `.pkt` files and documentation.

Cisco-Packet-Tracer-Projects
│
├── Project-01-Accounts-Delivery
├── Project-02-Branch-Network
├── Project-03-Enterprise-Network-Design
├── Project-04-Campus-Network
├── Project-05-Bank-Network
├── Project-06-Enterprise-Network-Infrastructure-Design
├── Project-07-Hospital-Network
└── LICENSE

yaml
Copy code

---

## Project Summary

### Project 01 – Accounts & Delivery Network
- Basic departmental LAN design
- Static IP addressing
- Connectivity verification

### Project 02 – Branch Office Network
- Branch-level topology
- Subnetting and routing implementation

### Project 03 – Enterprise Network Design
- VLAN segmentation
- Inter-VLAN routing
- Hierarchical architecture

### Project 04 – Campus Network
- Multi-department campus environment
- Multiple VLANs and subnets

### Project 05 – Bank Network
- Enterprise-grade network simulation
- Department-based segmentation

### Project 06 – Enterprise Network Infrastructure Design
- Advanced enterprise infrastructure concepts

### Project 07 – Hospital Network
- Hospital network simulation
- Reliable and structured departmental connectivity

---

## Troubleshooting Scenarios (NOC Perspective)

The following scenarios represent **common incidents handled by Network Operations Center (NOC) teams**.

### Scenario Examples
- Inter-VLAN communication failure
- DHCP address assignment failure
- Switch port down / no connectivity
- Routing failure between networks
- Intermittent network connectivity

Each scenario follows a structured troubleshooting approach:
- Incident identification
- Impact assessment
- Root cause analysis
- Resolution and validation

---

## Incident Ticket Format (NOC / ITIL Style)

```text
Ticket ID: INC-2025-001
Priority: P2 – High
Category: Network Connectivity
Service Affected: Internal LAN
Status: Resolved
Key Elements:

Incident description

Impact assessment

Initial diagnosis (NOC L1)

Investigation & resolution (NOC L2)

Validation and closure notes

Troubleshooting Matrix (Operational View)
Issue	Symptoms	Possible Causes	Verification Commands	Resolution
Inter-VLAN Failure	Cannot ping across VLANs	Missing routing, trunk issue	show vlan brief
show interfaces trunk	Configure inter-VLAN routing
DHCP Failure	No IP assigned	DHCP disabled, helper missing	show ip dhcp binding	Enable DHCP / helper address
Port Down	No connectivity	Interface shutdown	show interfaces status	Enable interface
Routing Failure	Network unreachable	Missing route	show ip route	Add correct route
Intermittent Issue	Packet loss	Duplex/STP issue	show interfaces	Fix duplex / STP

ITIL Incident Management Alignment
This portfolio aligns with the ITIL Incident Management lifecycle:

Incident Identification

Categorization & Prioritization

Initial Diagnosis (NOC L1)

Investigation & Diagnosis (NOC L2)

Resolution & Recovery

Incident Closure

Post-Incident Review

This demonstrates readiness for enterprise operational environments.

How to Use
Clone the repository:

bash
Copy code
git clone https://github.com/ekpurwanto/Cisco-Packet-Tracer-Projects.git
Open Cisco Packet Tracer.

Navigate to a project folder.

Open the .pkt file and review topology and configurations.

Verify connectivity using:

ping

routing table checks

VLAN verification

Professional Use Case
This repository serves as:

CCNA practice lab

Network engineering portfolio

NOC operational showcase

Supporting material for job applications

License
This project is licensed under the MIT License.
Free to use for educational and professional purposes.

Author
Eko Purwanto
Data Science Enthusiast | IT Support | Python • SQL • VMware | Networking & IT Infrastructure Enthusiast | Former Content Manager
GitHub: https://github.com/ekpurwanto

