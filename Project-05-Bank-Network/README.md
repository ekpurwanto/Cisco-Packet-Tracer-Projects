# 📌 Enterprise Network Design & Implementation  
**Company Limited – Banking & Insurance**

---

## 📘 Overview

This project presents the design and implementation of an **enterprise network** for **Company Limited**, a banking and insurance company expanding its operations.

The company occupies a **four-story office building**, where each floor hosts **three departments**.  
The network design follows the **Hierarchical Network Model** consisting of **Core, Distribution, and Access layers**, and is fully implemented using **Cisco Packet Tracer**.

This project serves as an **academic and professional case study**, emphasizing real-world enterprise networking best practices including:

- Scalability  
- Redundancy  
- Security  
- Efficient network management  

---

## 🏗️ Building & Department Structure

- **Total Floors:** 4  
- **Departments per Floor:** 3  
- **Total Departments:** 12  
- **Users per Department:** ~60 (wired & wireless)

Each department includes:
- Wired PCs  
- Network printer  
- Wireless users via Access Point  

A **dedicated Server Room** hosts centralized services such as:
- DHCP Server  
- Application Servers  

---

## 🎯 Project Requirements

### 1️⃣ Network Design & Modeling
The network topology is designed using:
- Microsoft Visio  
- Visual Paradigm  
- Draw.io  

The design clearly illustrates:
- Floors and departments  
- Core, Distribution, and Access layers  
- Redundant interconnections  

---

### 2️⃣ Network Simulation
The topology is implemented and tested using:
- **Cisco Packet Tracer** (Primary)  
- **GNS3** (Optional)

---

### 3️⃣ Network Architecture

The network follows the **Hierarchical Network Model**:

#### 🔹 Core Layer
- Enterprise routers  
- Backbone routing and connectivity  

#### 🔹 Distribution Layer
- Layer-3 switches  
- Inter-VLAN routing  
- Policy enforcement  

#### 🔹 Access Layer
- Layer-2 switches  
- End-device connectivity  

✔ Redundancy is implemented at all layers for high availability.

---

### 4️⃣ Routing
- Dynamic routing using **OSPF (Open Shortest Path First)**  
- Automatic route advertisement  
- Fast convergence and scalability  

---

### 5️⃣ Devices & Connectivity
- One router per floor  
- Routers interconnected using serial links  
- Redundant connections between routers and distribution switches  
- Access switches connected to distribution switches  

---

### 6️⃣ VLAN & IP Addressing
- One VLAN per department  
- Proper IP planning and subnetting  
- VLAN segmentation improves:
  - Security  
  - Performance  
  - Broadcast control  

---

### 7️⃣ DHCP & Servers
- Centralized **DHCP Server** (Server Room)  
- DHCP dynamically assigns IPv4 addresses  
- Additional servers:
  - HTTP Server  
  - Email Server  

---

### 8️⃣ Wireless Networking
Each department includes:
- One Wireless Access Point  
- Wireless clients (smartphones & laptops)

Wireless users are integrated into the same VLAN architecture as wired devices.

---

### 9️⃣ Security
Basic security measures:
- Device hardening  
- SSH for remote management  
- VLAN-based segmentation  

---

### 🔟 Testing & Verification
The network is tested for:
- Inter-VLAN communication  
- End-to-end connectivity  
- DHCP address allocation  
- OSPF convergence  

---

## 🧠 Network Design Summary

### 🔹 Core Layer
- 4 Routers (one per floor)  
- Redundant interconnections  
- OSPF enabled  

### 🔹 Distribution Layer
- Layer-3 switches per floor  
- Inter-VLAN routing  
- Access to Core layer  

### 🔹 Access Layer
- One access switch per department  
- Connects PCs, printers, and APs  

---

## 🖥️ End Devices per Department

| Device                  | Quantity |
|-------------------------|----------|
| PCs                     | Multiple |
| Printer                 | 1        |
| Wireless Access Point   | 1        |
| Smartphones / Laptops   | Multiple |

---

## 🛠️ Tools Used

- **Microsoft Visio** – Topology design  
- **Cisco Packet Tracer** – Network simulation  

---

## 🖼️ Network Topology Diagram
The diagram includes:
- Floors (1–4)  
- Core, Distribution, and Access layers  
- Department-based access switches  
- Redundant links  

Exported in **PNG format** for documentation.

---

# ⚙️ Configuration Phase  
**Enterprise Network Implementation – Cisco Packet Tracer**

This phase focuses on actual device configuration and validation.

---

## 🎯 Configuration Objectives
- VLAN segmentation per department  
- Inter-VLAN routing on Layer-3 switches  
- Centralized DHCP deployment  
- OSPF routing configuration  
- Secure management using SSH  
- End-to-end connectivity verification  

---

## 🧱 VLAN & Department Mapping

| VLAN ID | Department        | Floor |
|--------|-------------------|-------|
| 10     | Management        | 1     |
| 20     | Research          | 1     |
| 30     | Human Resource    | 1     |
| 40     | Marketing         | 2     |
| 50     | Accounts          | 2     |
| 60     | Finance           | 2     |
| 70     | Logistics         | 3     |
| 80     | Customer Care     | 3     |
| 90     | Guest             | 3     |
| 100    | Admin             | 4     |
| 110    | ICT               | 4     |
| 120    | Server Room       | 4     |

---

## 📊 IP Addressing & VLAN Mapping

Each VLAN uses a **/26 subnet (255.255.255.192)**.

| VLAN | Department       | Network Address        | Subnet Mask         | Default Gateway     |
|-----|------------------|------------------------|---------------------|---------------------|
| 10  | Management       | 192.168.10.0/26        | 255.255.255.192     | 192.168.10.1        |
| 20  | Research         | 192.168.10.64/26       | 255.255.255.192     | 192.168.10.65       |
| 30  | Human Resource   | 192.168.10.128/26      | 255.255.255.192     | 192.168.10.129      |
| 40  | Marketing        | 192.168.10.192/26      | 255.255.255.192     | 192.168.10.193      |
| 50  | Accounts         | 192.168.11.0/26        | 255.255.255.192     | 192.168.11.1        |
| 60  | Finance          | 192.168.11.64/26       | 255.255.255.192     | 192.168.11.65       |
| 70  | Logistics        | 192.168.11.128/26      | 255.255.255.192     | 192.168.11.129      |
| 80  | Customer Care    | 192.168.11.192/26      | 255.255.255.192     | 192.168.11.193      |
| 90  | Guest            | 192.168.12.0/26        | 255.255.255.192     | 192.168.12.1        |
| 100 | Admin            | 192.168.12.64/26       | 255.255.255.192     | 192.168.12.65       |
| 110 | ICT              | 192.168.12.128/26      | 255.255.255.192     | 192.168.12.129      |
| 120 | Server Room      | 192.168.12.192/26      | 255.255.255.192     | 192.168.12.193      |

---

## 🌐 Router & Layer-3 Point-to-Point Links

| Link Description          | Network         | IP Assignment |
|---------------------------|-----------------|---------------|
| Core ↔ Dist Floor 1       | 10.10.10.0/30   | .1 / .2       |
| Core ↔ Dist Floor 2       | 10.10.10.4/30   | .5 / .6       |
| Core ↔ Dist Floor 3       | 10.10.10.8/30   | .9 / .10      |
| Core ↔ Dist Floor 4       | 10.10.10.12/30  | .13 / .14     |

---

## 🔁 Routing Configuration
- OSPF Area 0 on all routers and L3 switches  
- VLAN and P2P networks advertised dynamically  

---

## 📡 DHCP Configuration
- Centralized DHCP Server (VLAN 120)  
- One DHCP pool per VLAN  
- `ip helper-address` on all SVIs  

---

# 🔐 Security & Hardening Phase

## 🎯 Security Objectives
- Secure device access  
- Encrypted remote management (SSH)  
- Port security  
- Reduced attack surface  

---

## 🛡️ Security Policies Implemented
- Console & VTY protection  
- SSH-only access  
- Encrypted passwords  
- VLAN segmentation  
- Banner warnings  

---

## 📘 Command Reference per Device

### 🔧 Router Security Configuration

hostname CORE-RTR
no ip domain-lookup
service password-encryption
enable secret class

🔧 Layer-3 Switch
hostname DIST-L3-SW
ip routing
service password-encryption

🔧 Access Switch
hostname ACCESS-SW
switchport port-security
spanning-tree portfast

🧪 Verification Commands
show vlan brief
show ip route
show ip ospf neighbor
show ip dhcp binding
show port-security
ping
tracert

📌 Best Practices Applied

✔ SSH over Telnet
✔ Disable unused ports
✔ Enable password encryption
✔ VLAN-based isolation

🚀 Next Phase

ACL implementation

Guest VLAN isolation

Firewall integration

Network monitoring

Project Level: Intermediate – Advanced
Project Type: Enterprise Network Design

🔐 Secure networks build reliable systems.