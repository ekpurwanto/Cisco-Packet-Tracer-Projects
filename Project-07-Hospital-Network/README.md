<div align="center">

# 🏥 Enterprise Network Project 7
### Hospital Network Infrastructure

[![Cisco Packet Tracer](https://img.shields.io/badge/Cisco-Packet_Tracer-1BA0D7?style=for-the-badge&logo=cisco&logoColor=white)](https://www.netacad.com/courses/packet-tracer)
[![OSPF](https://img.shields.io/badge/Routing-OSPF-FF6B00?style=for-the-badge)](https://github.com)
[![IPsec VPN](https://img.shields.io/badge/Security-IPsec_VPN-00C853?style=for-the-badge&logo=openvpn&logoColor=white)](https://github.com)
[![License](https://img.shields.io/badge/License-Educational-blue?style=for-the-badge)](LICENSE)

*A comprehensive enterprise network design implementing hierarchical topology, OSPF routing, IPsec VPN, and advanced security features*

[Features](#-key-features) • [Architecture](#-network-architecture) • [Technologies](#-technologies-implemented) • [Getting Started](#-getting-started) • [Documentation](#-configuration-guide)

</div>

---

## 📑 Table of Contents

- [Project Overview](#-project-overview)
- [Key Features](#-key-features)
- [Network Requirements](#-network-requirements)
- [Network Architecture](#-network-architecture)
- [Network Topology](#️-network-topology)
- [IP Addressing Scheme](#-ip-addressing-scheme)
- [Technologies Implemented](#-technologies-implemented)
- [Getting Started](#-getting-started)
- [Configuration Guide](#-configuration-guide)
- [Testing & Verification](#-testing--verification)
- [Troubleshooting](#-troubleshooting)
- [Network Statistics](#-network-statistics)
- [Skills Demonstrated](#-skills-demonstrated)
- [Contributing](#-contributing)
- [License](#-license)
- [Contact](#-contact)
- [Acknowledgments](#-acknowledgments)

---

## 📋 Project Overview

This project involves designing and implementing a secure, redundant enterprise network for **Health Services**, a healthcare provider in Australia operating across two locations (Headquarters and Branch Hospital) within the same city, 20 kilometers apart.

The network follows industry best practices with a hierarchical design model, implementing advanced technologies including IPsec VPN tunneling, OSPF dynamic routing, centralized DHCP services, comprehensive wireless coverage, and multi-layered security features.

---

## ✨ Key Features

- 🔒 **Site-to-Site IPsec VPN** - Encrypted communication between HQ and Branch with AES-256
- 🌐 **Dynamic Routing** - OSPF implementation across the enterprise (Area 0)
- 📡 **Wireless Infrastructure** - Complete Wi-Fi coverage with WPA2-PSK for all departments
- 🔐 **Multi-layer Security** - ACLs, Port Security, SSH, NAT/PAT, and encrypted passwords
- 🏗️ **Hierarchical Design** - Scalable 3-tier network architecture (Core, Distribution, Access)
- 🔄 **High Availability** - Redundant connections and dual ISP links per site
- 📊 **Centralized Services** - DHCP, DNS, Web, and Email servers in dedicated site
- 🎯 **VLAN Segmentation** - 12 VLANs for departmental isolation
- 🔀 **Inter-VLAN Routing** - Layer 3 switches with SVI configuration
- 🌍 **Internet Connectivity** - PAT implementation with failover capability

---

## 🏥 Network Requirements

### Locations & Departments

#### **Headquarters (HQ)** - 6 Departments
| Department | Code | Users |
|------------|------|-------|
| Medical Lead Operation and Consultancy Services | MLOCS | ~60 |
| Medical Emergency and Response | MER | ~60 |
| Medical Records Management | MRM | ~60 |
| Information Technology | IT | ~60 |
| Customer Services | CS | ~60 |
| Guest/Waiting Area | GUEST | ~60 |

#### **Branch Hospital** - 6 Departments
| Department | Code | Users |
|------------|------|-------|
| Operations & Hospital Labs | NSO | ~30 |
| Health Australia Labs | HL | ~30 |
| Human Resources | HR | ~30 |
| Marketing | MK | ~30 |
| Finance | FIN | ~30 |
| Guest/Waiting Area | GUEST | ~30 |

#### **Server Site** (At HQ)
- Separate location connected via access switch
- Hosts: DHCP Server, DNS Server, Web Server, Email Server
- Static IP addressing with /28 subnet

---

## 🏗️ Network Architecture

### Hierarchical Design Model
```
┌─────────────────────────────────────────────────────────────┐
│                     CORE LAYER                               │
│  • 2 Core Routers (HQ-Router, Branch-Router)                │
│  • 4 ISP Connections (2 per router for redundancy)          │
│  • IPsec VPN Tunnel (Site-to-Site Encryption)              │
└─────────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────────┐
│                  DISTRIBUTION LAYER                          │
│  • 4 Multilayer Switches (L3 Switches)                      │
│  • 2 per location (HQ-ML-SW1/2, Branch-ML-SW1/2)           │
│  • OSPF Routing + Inter-VLAN Routing                        │
└─────────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────────┐
│                    ACCESS LAYER                              │
│  • 12 Access Switches (6 per location)                      │
│  • 1 Switch per department                                   │
│  • VLAN assignment + Port Security                          │
└─────────────────────────────────────────────────────────────┘
                            │
┌─────────────────────────────────────────────────────────────┐
│                    END DEVICES                               │
│  • PCs, Laptops, Printers, Smartphones                      │
│  • Wireless Access Points (1 per department)                │
│  • DHCP-assigned IP addresses                               │
└─────────────────────────────────────────────────────────────┘
```

### Device Count Summary
- **Routers:** 4 (2 Core + 2 ISPs)
- **Multilayer Switches:** 4 (Layer 3)
- **Access Switches:** 13 (12 departments + 1 server site)
- **Wireless Access Points:** 12
- **Servers:** 4 (DHCP, DNS, Web, Email)
- **End Devices:** 24+ workstations and mobile devices

---

## 🗺️ Network Topology
```
                    ┌─────────┐     ┌─────────┐
                    │  ISP 1  │     │  ISP 2  │
                    └────┬────┘     └────┬────┘
                         │               │
            ┌────────────┴───────────────┴────────────┐
            │          (Serial DCE Interfaces)         │
            │                                          │
      ┌─────▼─────┐                            ┌─────▼─────┐
      │ HQ Router │◄──────IPsec VPN Tunnel────►│Branch Rtr │
      │192.168.    │    (AES-256 Encrypted)     │192.168.   │
      │102.82/30   │                            │102.90/30  │
      └─────┬─────┘                             └─────┬─────┘
            │                                          │
    ┌───────┴───────┐                          ┌──────┴──────┐
    │  GigE Links   │                          │  GigE Links │
    │               │                          │             │
┌───▼────┐      ┌───▼────┐                ┌───▼────┐   ┌───▼────┐
│HQ-ML   │      │HQ-ML   │                │Branch  │   │Branch  │
│Switch1 │──────│Switch2 │                │ML-SW1  │───│ML-SW2  │
│(L3)    │      │(L3)    │                │(L3)    │   │(L3)    │
└───┬────┘      └───┬────┘                └───┬────┘   └───┬────┘
    │               │                          │           │
    └─┬──┬──┬──┬────┴──┬──┐              └─┬──┬──┬──┬────┴──┬──┐
      │  │  │  │       │  │                │  │  │  │       │  │
    ┌─▼┐┌▼┐┌▼┐┌▼┐    ┌▼┐┌▼┐             ┌─▼┐┌▼┐┌▼┐┌▼┐    ┌▼┐┌▼┐
    │ML││ME││MR││IT│    │CS││G│             │NS││HL││HR││MK│    │FI││G│
    │OC││R ││M ││  │    │  ││U│             │O ││  ││  ││  │    │N ││U│
    │S ││  ││  ││  │    │  ││E│             │  ││  ││  ││  │    │  ││E│
    └──┘└─┘└─┘└─┘    └─┘└─┘             └─┘└─┘└─┘└─┘    └─┘└─┘
    VLAN VLAN VLAN VLAN VLAN VLAN        VLAN VLAN VLAN VLAN VLAN VLAN
     10   20   30   40   50   60          80   90  100  110  120  130

            ┌──────────────────────┐
            │   Server Site (HQ)   │
            │  ┌────────────────┐  │
            │  │ DHCP: .67      │  │
            │  │ DNS:  .68      │  │
            │  │ Web:  .70      │  │
            │  │ Email:.69      │  │
            │  └────────────────┘  │
            │  192.168.102.64/28   │
            └──────────────────────┘
```

**Legend:**
- `◄──►` : IPsec VPN Tunnel (Encrypted)
- `──` : Physical Connections
- VLAN XX : Virtual LAN Segmentation

---

## 📊 IP Addressing Scheme

### Network: 192.168.100.0/24 (Primary Block)

#### HQ Network (60 users per department - /26 notation)

| Department | Network | First Usable | Last Usable | Broadcast | Gateway | VLAN |
|------------|---------|--------------|-------------|-----------|---------|------|
| MLOCS | 192.168.100.0/26 | .1 | .62 | .63 | .1 | 10 |
| MER | 192.168.100.64/26 | .65 | .126 | .127 | .65 | 20 |
| MRM | 192.168.100.128/26 | .129 | .190 | .191 | .129 | 30 |
| IT | 192.168.100.192/26 | .193 | .254 | .255 | .193 | 40 |
| CS | 192.168.101.0/26 | .1 | .62 | .63 | .1 | 50 |
| Guest | 192.168.101.64/26 | .65 | .126 | .127 | .65 | 60 |

#### Branch Network (30 users per department - /27 notation)

| Department | Network | First Usable | Last Usable | Broadcast | Gateway | VLAN |
|------------|---------|--------------|-------------|-----------|---------|------|
| NSO | 192.168.101.128/27 | .129 | .158 | .159 | .129 | 80 |
| HL | 192.168.101.160/27 | .161 | .190 | .191 | .161 | 90 |
| HR | 192.168.101.192/27 | .193 | .222 | .223 | .193 | 100 |
| MK | 192.168.101.224/27 | .225 | .254 | .255 | .225 | 110 |
| FIN | 192.168.102.0/27 | .1 | .30 | .31 | .1 | 120 |
| Guest | 192.168.102.32/27 | .33 | .62 | .63 | .33 | 130 |

#### Server Site Network (/28 notation - 10 hosts)

| Device | IP Address | Subnet Mask | Gateway | VLAN |
|--------|------------|-------------|---------|------|
| Network | 192.168.102.64/28 | 255.255.255.240 | - | 70 |
| Gateway | 192.168.102.65 | 255.255.255.240 | - | 70 |
| DHCP Server | 192.168.102.67 | 255.255.255.240 | .65 | 70 |
| DNS Server | 192.168.102.68 | 255.255.255.240 | .65 | 70 |
| Email Server | 192.168.102.69 | 255.255.255.240 | .65 | 70 |
| Web Server | 192.168.102.70 | 255.255.255.240 | .65 | 70 |

#### Inter-Router Links (/30 notation - Point-to-Point)

| Link | Network | Router 1 | Router 2 | Purpose |
|------|---------|----------|----------|---------|
| HQ-Branch | 192.168.102.88/30 | .89 | .90 | VPN Tunnel Primary |
| HQ-ISP1 | 195.136.17.0/30 | .1 | .2 | Internet Link 1 |
| HQ-ISP2 | 195.136.17.4/30 | .5 | .6 | Internet Link 2 (Backup) |
| Branch-ISP1 | 195.136.17.8/30 | .9 | .10 | Internet Link 1 |
| Branch-ISP2 | 195.136.17.12/30 | .13 | .14 | Internet Link 2 (Backup) |

#### Route Aggregation Summary (for VPN ACLs)

| Location | Aggregated Network | Individual Networks Covered | Hosts |
|----------|-------------------|----------------------------|-------|
| HQ Block 1 | 192.168.100.0/24 | 100.0/26, 100.64/26, 100.128/26, 100.192/26 | 256 |
| HQ Block 2 | 192.168.101.0/25 | 101.0/26, 101.64/26 | 128 |
| Branch All | 192.168.101.128/25 | All 6 branch subnets | 128 |

---

## 🔧 Technologies Implemented

### 1. VLANs (Virtual Local Area Networks)

**Configuration Overview:**
- **12 VLANs Total** for departmental segmentation
- **HQ VLANs:** 10, 20, 30, 40, 50, 60
- **Branch VLANs:** 80, 90, 100, 110, 120, 130
- **Server VLAN:** 70

**Benefits:**
- Separate broadcast domains per department
- Enhanced security through network segmentation
- Better traffic management
- Simplified administration

**Sample Configuration:**
```cisco
! VLAN Creation
vlan 10
 name MLOCS
vlan 20
 name MER
vlan 30
 name MRM

! Access Port Configuration
interface range fa0/3-24
 switchport mode access
 switchport access vlan 10

! Trunk Port Configuration
interface range fa0/1-2
 switchport mode trunk
```

---

### 2. Inter-VLAN Routing

**Implementation Methods:**

#### A. Router-on-a-Stick (Server Site)
```cisco
! Remove IP from physical interface
interface gig0/0
 no ip address
 no shutdown

! Configure sub-interfaces
interface gig0/0.70
 encapsulation dot1Q 70
 ip address 192.168.102.65 255.255.255.240
```

#### B. Switched Virtual Interfaces (L3 Switches)
```cisco
! Enable routing
ip routing

! Configure SVIs
interface vlan 10
 ip address 192.168.100.1 255.255.255.192
 ip helper-address 192.168.102.67
 no shutdown

interface vlan 20
 ip address 192.168.100.65 255.255.255.192
 ip helper-address 192.168.102.67
 no shutdown
```

**IP Helper-Address:**
- Relays DHCP broadcasts to centralized server
- Configured on all VLAN interfaces
- Points to DHCP server: 192.168.102.67

---

### 3. OSPF (Open Shortest Path First)

**Configuration Parameters:**
- **Process ID:** 10
- **Area:** 0 (Backbone)
- **Network Type:** Broadcast (Ethernet), Point-to-Point (Serial)
- **Router ID:** Auto-assigned based on highest IP

**Implementation:**
```cisco
! OSPF Configuration on Routers
router ospf 10
 network 192.168.100.0 0.0.0.63 area 0
 network 192.168.100.64 0.0.0.63 area 0
 network 192.168.100.128 0.0.0.63 area 0
 network 192.168.100.192 0.0.0.63 area 0
 network 192.168.101.0 0.0.0.63 area 0
 network 192.168.101.64 0.0.0.63 area 0
 network 192.168.102.80 0.0.0.3 area 0

! OSPF on Multilayer Switches
ip routing
router ospf 10
 network 192.168.100.0 0.0.0.255 area 0
 network 192.168.101.0 0.0.0.127 area 0
```

**Verification Commands:**
```cisco
show ip ospf neighbor
show ip ospf database
show ip route ospf
show ip protocols
```

---

### 4. DHCP Configuration

**Centralized DHCP Server Setup:**
```cisco
! DHCP Pool for MLOCS Department
ip dhcp pool MLOCS_POOL
 network 192.168.100.0 255.255.255.192
 default-router 192.168.100.1
 dns-server 192.168.102.68
 lease 7

! DHCP Pool for MER Department
ip dhcp pool MER_POOL
 network 192.168.100.64 255.255.255.192
 default-router 192.168.100.65
 dns-server 192.168.102.68
 lease 7

! Exclude gateway addresses
ip dhcp excluded-address 192.168.100.1
ip dhcp excluded-address 192.168.100.65
```

**DHCP Pools Summary:**
- **Total Pools:** 12 (one per department)
- **Lease Time:** 7 days
- **DNS Server:** 192.168.102.68 (centralized)
- **Gateway:** VLAN interface on L3 switch

---

### 5. IPsec VPN Tunnel (Site-to-Site)

**Configuration Overview:**

#### Phase 1: ISAKMP Policy (IKE)
```cisco
! Enable security license
license boot module c2900 technology-package securityk9
do reload

! Create ISAKMP Policy
crypto isakmp policy 10
 encryption aes 256
 authentication pre-share
 group 5
 exit

! Configure Pre-Shared Key
crypto isakmp key VPN address 192.168.102.90
```

#### Phase 2: IPsec Transform Set
```cisco
! Create Transform Set
crypto ipsec transform-set VPN_SET esp-aes esp-sha-hmac

! Create Crypto Map
crypto map VPN_MAP 10 ipsec-isakmp
 description VPN Connection to Branch/HQ Network
 set peer 192.168.102.90
 set transform-set VPN_SET
 match address 110
```

#### Apply Crypto Map to Interface
```cisco
interface serial 0/0/0
 crypto map VPN_MAP
```

#### Access Control List for VPN Traffic
```cisco
! Extended ACL for interesting traffic
access-list 110 permit ip 192.168.100.0 0.0.0.255 192.168.101.128 0.0.0.127
access-list 110 permit ip 192.168.101.0 0.0.0.127 192.168.101.128 0.0.0.127
```

**VPN Parameters:**
- **Encryption:** AES-256
- **Hashing:** SHA-HMAC
- **Authentication:** Pre-Shared Key
- **Diffie-Hellman Group:** 5
- **Protocol:** ESP (Encapsulating Security Payload)

**Verification:**
```cisco
show crypto isakmp sa
show crypto ipsec sa
show crypto map
```

**Expected Output:**
```
Crypto map tag: VPN_MAP, local addr 192.168.102.89
   protected vlan: 
   local  ident (addr/mask/prot/port): (192.168.100.0/0.0.0.255/0/0)
   remote ident (addr/mask/prot/port): (192.168.101.128/0.0.0.127/0/0)
   #pkts encaps: 15, #pkts encrypt: 15, #pkts digest: 15
   #pkts decaps: 14, #pkts decrypt: 14, #pkts verify: 14
```

---

### 6. NAT/PAT (Port Address Translation)

**Configuration on HQ Router:**
```cisco
! Define inside interfaces
interface range gig0/0 - 2
 ip nat inside

! Define outside interfaces
interface serial 0/1/0
 ip nat outside
interface serial 0/2/1
 ip nat outside

! Configure PAT with overload
ip nat inside source list 1 interface serial 0/1/0 overload
ip nat inside source list 1 interface serial 0/2/1 overload

! Access Control List for NAT
access-list 1 permit 192.168.100.0 0.0.0.63
access-list 1 permit 192.168.100.64 0.0.0.63
access-list 1 permit 192.168.100.128 0.0.0.63
access-list 1 permit 192.168.100.192 0.0.0.63
access-list 1 permit 192.168.101.0 0.0.0.63
access-list 1 permit 192.168.101.64 0.0.0.63
```

**Configuration on Branch Router:**
```cisco
! Similar configuration with Branch subnets
interface range gig0/0 - 1
 ip nat inside

interface serial 0/1/1
 ip nat outside
interface serial 0/2/0
 ip nat outside

ip nat inside source list 1 interface serial 0/1/1 overload
ip nat inside source list 1 interface serial 0/2/0 overload

access-list 1 permit 192.168.101.128 0.0.0.31
access-list 1 permit 192.168.101.160 0.0.0.31
access-list 1 permit 192.168.101.192 0.0.0.31
access-list 1 permit 192.168.101.224 0.0.0.31
access-list 1 permit 192.168.102.0 0.0.0.31
access-list 1 permit 192.168.102.32 0.0.0.31
```

**Verification:**
```cisco
show ip nat translations
show ip nat statistics
```

---

### 7. Access Control Lists (ACLs)

**Types Implemented:**

#### A. Standard ACL (for NAT)
```cisco
access-list 1 permit 192.168.100.0 0.0.0.63
access-list 1 permit 192.168.100.64 0.0.0.63
```

#### B. Extended ACL (for VPN)
```cisco
access-list 110 permit ip 192.168.100.0 0.0.0.255 192.168.101.128 0.0.0.127
access-list 110 permit ip 192.168.101.0 0.0.0.127 192.168.101.128 0.0.0.127
```

**Purpose:**
- Control traffic flow
- Define interesting traffic for VPN encryption
- Permit/deny specific communications
- Network security enhancement

---

### 8. Wireless Network Configuration

**Access Point Setup:**
```cisco
! On Access Point (GUI Configuration)
Port 1 Configuration:
 SSID: [Department_Name]
 Authentication: WPA2-PSK
 Passphrase: cisco123
 Encryption: AES
```

**Client Configuration:**
1. Install wireless module (WPC-300N) on laptops
2. Connect to SSID
3. Enter WPA2 password
4. Obtain IP via DHCP automatically

**Wireless Standards:**
- **12 Access Points** (one per department)
- **Security:** WPA2-PSK with AES encryption
- **SSID:** Department-specific naming
- **Password:** cisco123 (uniform for simplicity)

---

### 9. Switch Port Security

**Configuration on Server Site Switch:**
```cisco
! Configure port security on server connections
interface range fa0/3-6
 switchport port-security
 switchport port-security maximum 1
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
```

**Parameters:**
- **Maximum Devices:** 1 per port
- **MAC Learning:** Sticky (auto-learn and save)
- **Violation Mode:** Shutdown
- **Purpose:** Prevent unauthorized device connections

**Verification:**
```cisco
show port-security
show port-security interface fa0/3
```

---

### 10. SSH Configuration

**Secure Remote Management:**
```cisco
! Configure domain name
ip domain-name cisco.net

! Create local user
username admin password cisco

! Generate RSA keys
crypto key generate rsa
 1024

! Configure VTY lines
line vty 0 15
 login local
 transport input ssh
 exit

! Save configuration
do write
```

**SSH Parameters:**
- **Modulus:** 1024-bit RSA key
- **Authentication:** Local database
- **Access:** VTY lines 0-15
- **Protocol:** SSH only (Telnet disabled)

**Testing:**
```bash
ssh -l admin 192.168.100.1
```

---

### 11. Static Default Routing

**Primary and Backup Routes:**
```cisco
! HQ Router - Primary route via ISP1
ip route 0.0.0.0 0.0.0.0 195.136.17.2

! HQ Router - Backup route via ISP2 (higher AD)
ip route 0.0.0.0 0.0.0.0 195.136.17.6 70

! Branch Router - Primary route via ISP1
ip route 0.0.0.0 0.0.0.0 195.136.17.10

! Branch Router - Backup route via ISP2 (higher AD)
ip route 0.0.0.0 0.0.0.0 195.136.17.14 70
```

**Floating Static Route:**
- Backup route has higher Administrative Distance (70)
- Activates only when primary fails
- Provides redundancy for internet connectivity

---

### 12. Additional Security Features

#### Password Encryption
```cisco
service password-encryption
enable secret cisco
```

#### Console Security
```cisco
line console 0
 password cisco
 login
```

#### Banner Message
```cisco
banner motd #
***********************************************
*     AUTHORIZED ACCESS ONLY                  *
*   Unauthorized access is prohibited         *
*   All activities are monitored              *
***********************************************
#
```

#### Disable Unnecessary Services
```cisco
no ip domain-lookup
no cdp run (on sensitive interfaces)
```

---

## 🚀 Getting Started

### Prerequisites

- **Software:** Cisco Packet Tracer 7.3+ or 8.x
- **Knowledge:** CCNA-level networking concepts
- **Hardware:** PC with 4GB+ RAM recommended
- **OS:** Windows 10/11, macOS, or Linux

### Installation Steps

1. **Clone the Repository**
```bash
   git clone https://github.com/yourusername/Project-07-Hospital-Network.git
   cd Project-07-Hospital-Network
```

2. **Open Cisco Packet Tracer**
   - Launch Cisco Packet Tracer
   - File → Open
   - Navigate to `Hospital-Network-Design.pkt`

3. **Explore the Topology**
   - Review device configurations
   - Check IP addressing scheme
   - Verify VLAN assignments

### Quick Start Commands
```bash
# Verify OSPF neighbors
show ip ospf neighbor

# Check VPN tunnel status
show crypto ipsec sa

# Test inter-site connectivity
ping 192.168.101.171 source 192.168.100.70

# Verify NAT translations
show ip nat translations

# Check DHCP bindings
show ip dhcp binding

# View VLAN configuration
show vlan brief

# Check interface status
show ip interface brief
```

---

## 📘 Configuration Guide

### Step-by-Step Implementation

#### **Phase 1: Basic Device Configuration**
```cisco
enable
configure terminal
hostname HQ-Router
enable password cisco
no ip domain-lookup
banner motd #No Unauthorized Access#
line console 0
 password cisco
 login
service password-encryption
do write
```

#### **Phase 2: VLAN Configuration**
```cisco
! Create VLANs
vlan 10
 name MLOCS
vlan 20
 name MER

! Configure access ports
interface range fa0/3-24
 switchport mode access
 switchport access vlan 10

! Configure trunk ports
interface range fa0/1-2
 switchport mode trunk
```

#### **Phase 3: IP Addressing**
```cisco
! Routed port on L3 Switch
interface gig1/0/1
 no switchport
 ip address 192.168.102.82 255.255.255.252
 no shutdown

! SVI on L3 Switch
interface vlan 10
 ip address 192.168.100.1 255.255.255.192
 ip helper-address 192.168.102.67
 no shutdown
```

#### **Phase 4: OSPF Configuration**
```cisco
! On Router
router ospf 10
 network 192.168.100.0 0.0.0.255 area 0
 network 192.168.102.80 0.0.0.3 area 0

! On L3 Switch
ip routing
router ospf 10
 network 192.168.100.0 0.0.0.255 area 0

#### **Phase 5: DHCP Setup**
```cisco
! On DHCP Server (via GUI)
Services → DHCP
Pool Name: MLOCS_POOL
Default Gateway: 192.168.100.1
DNS Server: 192.168.102.68
Start IP: 192.168.100.6
Subnet Mask: 255.255.255.192
Maximum Users: 60
```

#### **Phase 6: IPsec VPN**
```cisco
! Phase 1 - ISAKMP
crypto isakmp policy 10
 encryption aes 256
 authentication pre-share
 group 5
crypto isakmp key VPN address 192.168.102.90

! Phase 2 - IPsec
crypto ipsec transform-set VPN_SET esp-aes esp-sha-hmac
crypto map VPN_MAP 10 ipsec-isakmp
 set peer 192.168.102.90
 set transform-set VPN_SET
 match address 110

! Apply to interface
interface serial 0/0/0
 crypto map VPN_MAP

! ACL for interesting traffic
access-list 110 permit ip 192.168.100.0 0.0.0.255 192.168.101.128 0.0.0.127
```

#### **Phase 7: NAT/PAT**
```cisco
! Define inside/outside
interface range gig0/0 - 2
 ip nat inside
interface serial 0/1/0
 ip nat outside

! Configure PAT
ip nat inside source list 1 interface serial 0/1/0 overload

! ACL for NAT
access-list 1 permit 192.168.100.0 0.0.0.63
```

#### **Phase 8: SSH Configuration**
```cisco
ip domain-name cisco.net
username admin password cisco
crypto key generate rsa
1024
line vty 0 15
 login local
 transport input ssh
```

#### **Phase 9: Port Security**
```cisco
interface fa0/3
 switchport port-security
 switchport port-security maximum 1
 switchport port-security mac-address sticky
 switchport port-security violation shutdown
```

#### **Phase 10: Wireless Setup**
Access Point Configuration (GUI):

Port 1 → SSID: MLOCS_Wireless
Authentication: WPA2-PSK
Password: cisco123

Client Configuration:

Install WPC-300N module
Desktop → PC Wireless
Connect to SSID
Enter password

---

## 🧪 Testing & Verification

### Connectivity Tests

#### 1. Intra-VLAN Communication
```bash
# From MLOCS PC to MLOCS Printer
ping 192.168.100.10
```

#### 2. Inter-VLAN Routing
```bash
# From MLOCS (VLAN 10) to MER (VLAN 20)
ping 192.168.100.70
```

#### 3. Inter-Site VPN Communication
```bash
# From HQ to Branch (encrypted)
ping 192.168.101.171
tracert 192.168.101.171
```

#### 4. Internet Connectivity
```bash
# Ping ISP gateway
ping 195.136.17.2
```

#### 5. DHCP Functionality
```bash
# On end device
ipconfig /release
ipconfig /renew
ipconfig
```

#### 6. Wireless Connectivity
```bash
# Check wireless connection
ipconfig
ping 192.168.100.1 (gateway)
```

### Verification Commands

#### Routing Verification
```cisco
show ip route
show ip route ospf
show ip protocols
show ip ospf neighbor
show ip ospf interface brief
```

#### VPN Verification
```cisco
show crypto isakmp sa
show crypto ipsec sa
show crypto map

! Expected output shows:
! - ISAKMP SA status: ACTIVE
! - Packets encaps/decaps: > 0
! - Peer address: 192.168.102.90
```

#### NAT Verification
```cisco
show ip nat translations
show ip nat statistics

! Check for:
! - Inside global/local mappings
! - Translation count
! - Hits on ACL
```

#### DHCP Verification
```cisco
show ip dhcp binding
show ip dhcp pool
show ip dhcp server statistics
```

#### VLAN Verification
```cisco
show vlan brief
show interfaces trunk
show spanning-tree vlan 10
```

#### Security Verification
```cisco
show port-security
show port-security interface fa0/3
show running-config | include password
show crypto key mypubkey rsa
```

### Performance Metrics

| Metric | Expected Result | Actual Result |
|--------|----------------|---------------|
| OSPF Convergence | < 10 seconds | ✅ Pass |
| VPN Tunnel Up | 100% uptime | ✅ Pass |
| DHCP Success Rate | 100% | ✅ Pass |
| Inter-VLAN Latency | < 5ms | ✅ Pass |
| Inter-Site Latency | < 50ms | ✅ Pass |
| Packet Loss | 0% | ✅ Pass |
| Wireless Association | < 3 seconds | ✅ Pass |

---

## 🔧 Troubleshooting

### Common Issues and Solutions

#### Issue 1: VPN Tunnel Not Establishing

**Symptoms:**
- `show crypto isakmp sa` shows no active sessions
- Ping across sites fails
- No encrypted packets in `show crypto ipsec sa`

**Solutions:**
```cisco
! 1. Verify peer reachability
ping 192.168.102.90

! 2. Check crypto configuration
show crypto isakmp policy
show crypto map

! 3. Verify interesting traffic ACL
show access-lists 110

! 4. Clear crypto sessions and retry
clear crypto sa
clear crypto isakmp

! 5. Enable debug (use cautiously)
debug crypto isakmp
debug crypto ipsec
! Remember to disable: undebug all
```

**Common Causes:**
- Mismatched pre-shared keys
- Incorrect peer IP address
- ACL not matching traffic
- Crypto map not applied to interface

---

#### Issue 2: No DHCP Address Assigned

**Symptoms:**
- Devices show 169.254.x.x (APIPA)
- `ipconfig` shows no gateway or DNS
- Cannot reach other networks

**Solutions:**
```cisco
! On DHCP Server
show ip dhcp binding
show ip dhcp pool
show ip dhcp conflict

! On L3 Switch
show ip interface vlan 10
! Verify ip helper-address is configured

! On Client
ipconfig /release
ipconfig /renew

! Check DHCP pool availability
! Verify pool is not exhausted
! Ensure gateway is in excluded-address list
```

**Common Causes:**
- IP helper-address missing on SVI
- DHCP pool exhausted
- Wrong subnet mask in pool
- DHCP server not reachable

---

#### Issue 3: Inter-VLAN Routing Not Working

**Symptoms:**
- Can ping within VLAN
- Cannot ping other VLANs
- Gateway not reachable

**Solutions:**
```cisco
! Verify IP routing is enabled
show ip route
show running-config | include ip routing

! Check SVI status
show ip interface brief | include Vlan

! Enable if needed
configure terminal
ip routing

! Verify SVI configuration
show running-config interface vlan 10

! Check for SVI shutdown
interface vlan 10
 no shutdown
```

**Common Causes:**
- `ip routing` not enabled on L3 switch
- SVIs in shutdown state
- Wrong IP address on SVI
- Missing VLAN in database

---

#### Issue 4: OSPF Neighbors Not Forming

**Symptoms:**
- `show ip ospf neighbor` shows empty
- Routes not learning dynamically
- Network isolation

**Solutions:**
```cisco
! Verify OSPF configuration
show ip protocols
show ip ospf interface

! Check network statements
show running-config | section router ospf

! Verify interface is in OSPF
show ip ospf interface brief

! Check for mismatched parameters
show ip ospf neighbor detail

! Common fixes
router ospf 10
 network 192.168.100.0 0.0.0.255 area 0
```

**Common Causes:**
- Mismatched area IDs
- Incorrect network statements
- Interface not included in OSPF
- Passive interface configured

---

#### Issue 5: NAT Not Translating

**Symptoms:**
- Internal devices cannot reach internet
- `show ip nat translations` is empty
- No hits on NAT ACL

**Solutions:**
```cisco
! Verify NAT configuration
show ip nat statistics
show ip nat translations

! Check interface NAT designation
show ip interface brief
! Look for "NAT inside" and "NAT outside"

! Verify ACL permits traffic
show access-lists 1

! Test translation
! Generate traffic from inside to outside
ping 8.8.8.8 source 192.168.100.10

! Check translation created
show ip nat translations

! Clear translations if needed
clear ip nat translation *
```

**Common Causes:**
- Wrong inside/outside designation
- ACL not permitting traffic
- Wrong interface in NAT statement
- Overload keyword missing

---

#### Issue 6: Wireless Clients Cannot Connect

**Symptoms:**
- SSID not visible
- Authentication fails
- IP address not assigned

**Solutions:**
Access Point:

   1. Verify AP is powered on
   2. Check SSID is broadcasting
   3. Verify WPA2 password: cisco123
   4. Ensure correct VLAN assignment

Client Device:

   1. Install WPC-300N module (power off first)
   2. Desktop → PC Wireless
   3. Refresh available networks
   4. Enter correct password
   5. Wait for DHCP assignment

Switch:
! Verify port to AP is access port
show interfaces fa0/X switchport
show vlan brief

---

#### Issue 7: Port Security Violation

**Symptoms:**
- Port shows err-disabled
- Link light is orange/amber
- Device cannot connect

**Solutions:**
```cisco
! Check port security status
show port-security interface fa0/3

! View violation information
show port-security

! Clear err-disabled state
configure terminal
interface fa0/3
 shutdown
 no shutdown
 exit

! Or globally enable auto-recovery
errdisable recovery cause psecure-violation
errdisable recovery interval 30
```

---

#### Issue 8: SSH Connection Refused

**Symptoms:**
- "Connection refused" error
- Cannot remotely manage devices
- Telnet works but SSH doesn't

**Solutions:**
```cisco
! Verify SSH is enabled
show ip ssh

! Check RSA keys
show crypto key mypubkey rsa

! Regenerate if needed
crypto key generate rsa
1024

! Verify VTY configuration
show running-config | section line vty

! Ensure correct configuration
line vty 0 15
 login local
 transport input ssh

! Create local user if missing
username admin privilege 15 password cisco
```

---

### Debug Commands (Use with Caution)
```cisco
! OSPF debugging
debug ip ospf events
debug ip ospf adj

! VPN debugging
debug crypto isakmp
debug crypto ipsec

! DHCP debugging
debug ip dhcp server events

! Always disable after troubleshooting
undebug all
```

---

### Performance Optimization Tips

1. **Enable spanning-tree portfast** on access ports
```cisco
   interface range fa0/3-24
    spanning-tree portfast
```

2. **Use VLAN pruning** on trunk links
```cisco
   switchport trunk allowed vlan 10,20,30,40,50,60
```

3. **Adjust OSPF timers** for faster convergence
```cisco
   interface gig0/0
    ip ospf hello-interval 5
    ip ospf dead-interval 20
```

4. **Implement QoS** for voice/video traffic (future enhancement)

---

## 📈 Network Statistics

### Infrastructure Summary

| Category | Count | Details |
|----------|-------|---------|
| **Routers** | 4 | 2 Core + 2 ISP |
| **L3 Switches** | 4 | Distribution layer |
| **L2 Switches** | 13 | 12 dept + 1 server |
| **Access Points** | 12 | One per department |
| **Servers** | 4 | DHCP, DNS, Web, Email |
| **VLANs** | 12 | Departmental segmentation |
| **Subnets** | 15+ | Including P2P links |
| **End Devices** | 24+ | PCs, laptops, printers, phones |

### IP Address Utilization

| Location | Allocated IPs | Used IPs | Utilization |
|----------|---------------|----------|-------------|
| HQ Network | 384 | ~200 | 52% |
| Branch Network | 192 | ~100 | 52% |
| Server Site | 16 | 4 | 25% |
| **Total** | **592** | **~304** | **51%** |

### VLAN Distribution

HQ Site (6 VLANs):
├── VLAN 10 (MLOCS) - 60 users
├── VLAN 20 (MER) - 60 users
├── VLAN 30 (MRM) - 60 users
├── VLAN 40 (IT) - 60 users
├── VLAN 50 (CS) - 60 users
└── VLAN 60 (Guest) - 60 users
Branch Site (6 VLANs):
├── VLAN 80 (NSO) - 30 users
├── VLAN 90 (HL) - 30 users
├── VLAN 100 (HR) - 30 users
├── VLAN 110 (MK) - 30 users
├── VLAN 120 (FIN) - 30 users
└── VLAN 130 (Guest) - 30 users
Server Site:
└── VLAN 70 (Servers) - 4 servers

### Link Types & Speeds

| Link Type | Count | Speed | Purpose |
|-----------|-------|-------|---------|
| Serial (DCE) | 6 | 64 Kbps | WAN links, VPN |
| GigabitEthernet | 20+ | 1 Gbps | LAN backbone |
| FastEthernet | 288 | 100 Mbps | Access layer |
| Wireless | 12 APs | 54 Mbps | Wi-Fi access |

### Security Implementations

| Feature | Devices | Coverage |
|---------|---------|----------|
| SSH | 8 (All mgmt devices) | 100% |
| Port Security | 1 switch | Server site |
| IPsec VPN | 2 routers | Site-to-site |
| NAT/PAT | 2 routers | All outbound |
| ACLs | 2 routers | VPN + NAT |
| Password Encryption | All devices | 100% |

---

## 🎓 Skills Demonstrated

### Network Design
- ✅ Hierarchical three-tier architecture
- ✅ IP addressing and subnetting (VLSM)
- ✅ Scalable network topology
- ✅ Redundancy and high availability
- ✅ Network segmentation strategies

### Routing & Switching
- ✅ VLAN creation and management
- ✅ Inter-VLAN routing (SVI & ROAS)
- ✅ OSPF dynamic routing protocol
- ✅ Static and default routing
- ✅ Route aggregation/summarization
- ✅ Layer 3 switching configuration

### Network Services
- ✅ DHCP server configuration
- ✅ DNS server setup
- ✅ Web and email server deployment
- ✅ IP helper-address configuration
- ✅ Service redundancy

### Security
- ✅ IPsec VPN (site-to-site)
- ✅ Crypto ISAKMP configuration
- ✅ Access Control Lists (Standard & Extended)
- ✅ Port security implementation
- ✅ SSH configuration and management
- ✅ NAT/PAT translation
- ✅ Password encryption
- ✅ Banner messages

### Wireless Networking
- ✅ Access point deployment
- ✅ WPA2-PSK authentication
- ✅ SSID configuration
- ✅ Wireless client setup
- ✅ DHCP for wireless devices

### Troubleshooting
- ✅ Connectivity testing (ping, traceroute)
- ✅ Route verification
- ✅ VPN tunnel debugging
- ✅ NAT translation analysis
- ✅ OSPF neighbor relationships
- ✅ DHCP lease verification

### Best Practices
- ✅ Documentation and labeling
- ✅ Naming conventions
- ✅ Security hardening
- ✅ Configuration backup
- ✅ Network monitoring readiness

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

### How to Contribute

1. **Fork the Project**
```bash
   git fork https://github.com/ekpurwanto/Project-07-Hospital-Network.git
```

2. **Create Feature Branch**
```bash
   git checkout -b feature/AmazingFeature
```

3. **Commit Your Changes**
```bash
   git commit -m 'Add some AmazingFeature'
```

4. **Push to Branch**
```bash
   git push origin feature/AmazingFeature
```

5. **Open Pull Request**

### Contribution Guidelines

- Follow Cisco best practices
- Document all changes
- Test configurations thoroughly
- Update README if needed
- Add comments to complex configurations

### Areas for Contribution

- 🎯 QoS implementation for voice/video
- 🔒 Enhanced security features (802.1X, TACACS+)
- 📊 Network monitoring (SNMP, Syslog)
- 🔄 IPv6 dual-stack implementation
- 🌐 BGP for ISP redundancy
- 🛡️ Firewall integration
- 📱 Guest portal for wireless
- 🔐 Certificate-based VPN

---

## 📄 License

This project is licensed under the **Educational Use License**.

Permission is granted to use this project for:
✅ Educational purposes
✅ Training and learning
✅ Personal development
✅ Portfolio demonstration
Restrictions:
❌ Commercial use without permission
❌ Redistribution without attribution
❌ Modification without proper credit
THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND.


## 🙏 Acknowledgments

Special thanks to:

- **Cisco Networking Academy** - For Packet Tracer and educational resources
- **CCNA Curriculum** - Foundation for network design principles
- **Network Engineering Community** - For continuous learning and support
- **Open Source Contributors** - For documentation and tools
- **Students & Trainees** - For feedback and improvement suggestions

### Resources Used

- [Cisco Packet Tracer](https://www.netacad.com/courses/packet-tracer)
- [Cisco IOS Documentation](https://www.cisco.com/c/en/us/support/ios-nx-os-software/ios-15-4m-t/products-installation-and-configuration-guides-list.html)
- [CCNA Study Materials](https://learningnetwork.cisco.com/s/ccna-exam-topics)
- [RFC 2409 - IKE](https://tools.ietf.org/html/rfc2409)
- [RFC 4301 - IPsec](https://tools.ietf.org/html/rfc4301)

---

### Learning Path

1. **Beginner:** Enterprise Projects 1-3
2. **Intermediate:** Enterprise Projects 4-5
3. **Advanced:** Enterprise Projects 6-7
4. **Expert:** Enterprise Project 8 (VoIP Implementation - Coming Soon)

### Recommended Reading

- "CCNA 200-301 Official Cert Guide" - Wendell Odom
- "Network Security First-Step" - Thomas M. Thomas
- "IP Routing Fundamentals" - Mark A. Sportack
- Cisco Press VPN Configuration Guides

---

## 🔄 Version History

### v1.0.0 (Current)
- ✅ Initial release
- ✅ Complete network implementation
- ✅ IPsec VPN configuration
- ✅ OSPF routing
- ✅ Full documentation


## 📊 Project Metrics

| Metric | Value |
|--------|-------|
| Total Configuration Lines | 1000+ |
| Implementation Time | 8-10 hours |
| Complexity Level | Advanced |
| CCNA Topics Covered | 15+ |
| Security Features | 8 |
| Routing Protocols | 2 (OSPF, Static) |
| Total Devices | 50+ |
| Network Segments | 12 VLANs |

---

<div align="center">

## ⭐ Star this repository if you find it helpful!


**© 2025 All Rights Reserved**

