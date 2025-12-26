# Enterprise Network Infrastructure Design

## 📌 Overview
This project presents the design and implementation of an enterprise network infrastructure for **Company Limited**, a banking and insurance company expanding its operations.

The company operates in a **four-story office building**, where **each floor hosts three departments**.  
The network is designed using the **Hierarchical Network Model** and implemented using **Cisco Packet Tracer** as part of an **academic and professional case study** focusing on real-world enterprise networking best practices.

---

## 🏗️ Network Architecture
The network follows the **Cisco Hierarchical Network Model**, which consists of:

### 1. Core Layer
- High-speed backbone connectivity  
- Inter-VLAN routing and WAN connections  
- Optimized for performance and redundancy  

### 2. Distribution Layer
- VLAN routing and policy enforcement  
- Security filtering and access control  
- Aggregation point between core and access layers  

### 3. Access Layer
- End-device connectivity (PCs, IP Phones, Printers)  
- VLAN segmentation per department  
- Port security and basic access controls  

---

## 🏢 Building & Department Layout
- **Total Floors:** 4  
- **Departments per Floor:** 3  
- **Total Departments:** 12  

Each department is assigned:
- A dedicated **VLAN**
- A specific **IP subnet**
- Managed access via access-layer switches  

---

## 🔧 Technologies & Tools
- **Cisco Packet Tracer**
- Cisco Routers & Switches (Layer 2 & Layer 3)
- VLAN & Trunking (IEEE 802.1Q)
- Inter-VLAN Routing
- Dynamic Routing Protocols (RIP v2 / OSPF where applicable)
- Access Control Lists (ACL)
- Basic Network Security Practices

---

## 🌐 IP Addressing Scheme
The network uses a **structured and scalable IP addressing plan**, ensuring:
- Clear subnet separation per VLAN
- Efficient IP utilization
- Easy troubleshooting and future expansion

> Detailed IP addressing tables can be found in the configuration section of this repository.

---

## 🔐 Security Design
Implemented security measures include:
- VLAN segmentation
- Trunk port restrictions
- Access Control Lists (ACL)
- Role-based network separation
- Secure management access

---

## 📁 Project Contents
├── configs/ # Router & Switch configurations
├── diagrams/ # Network topology diagrams
├── packet-tracer/ # Cisco Packet Tracer (.pkt) files
├── documentation/ # Technical documentation
└── README.md # Project overview


---

## 🎯 Project Objectives
- Design a scalable enterprise network
- Apply industry-standard network architecture
- Implement VLAN-based segmentation
- Demonstrate real-world enterprise networking concepts
- Provide clear documentation for learning and reference

---

## 📚 Use Case
This project is suitable for:
- Networking students
- Cisco Packet Tracer practice
- Enterprise network design reference
- Academic assignments and professional portfolios

---

## 📜 License
This project is released under the **MIT License**.  
You are free to use, modify, and distribute this project for educational and professional purposes.


## ⭐ Acknowledgment
Inspired by real-world enterprise networking standards and Cisco best practices.
