🇮🇩 DESKRIPSI PROYEK (Bahasa Indonesia)

Proyek ini bertujuan untuk merancang dan mengimplementasikan jaringan komputer sederhana menggunakan Cisco Packet Tracer yang menghubungkan dua departemen, yaitu ACCOUNTS dan DELIVERY.

Jaringan dibangun menggunakan 1 router dan 2 access layer switch, dengan skema subnetting dari jaringan 192.168.40.0.
Setiap departemen memiliki minimal dua PC dan satu printer, serta seluruh perangkat diuji konektivitasnya.

ENG PROJECT DESCRIPTION (English)

This project focuses on designing and implementing a simple computer network using Cisco Packet Tracer to connect two departments: ACCOUNTS and DELIVERY.

The network uses one router and two access layer switches, subnetted from the 192.168.40.0 network.
Each department contains at least two PCs and one printer, and full connectivity is verified.

🎯 PROJECT REQUIREMENTS
(🇮🇩) Kebutuhan Proyek

   - Menghubungkan departemen ACCOUNTS dan DELIVERY

    - Setiap departemen memiliki minimal 2 PC

    - Menggunakan router dan switch yang sesuai

    - Menggunakan network 192.168.40.0

    - Semua interface memiliki IP Address, Subnet Mask, dan Gateway

    - Menggunakan kabel yang sesuai

    - Menguji konektivitas jaringan

(ENG) Project Requirements

    - Connect ACCOUNTS and DELIVERY departments

    - Each department must have at least two PCs

    - Use appropriate routers and switches

    - Use network 192.168.40.0

    - Configure all interfaces with IP Address, Subnet Mask, and Gateway

    - Use proper cabling

    - Test network communication

🏗️ NETWORK TOPOLOGY (ASCII DIAGRAM)
                   ┌───────────────────┐
                   │      ROUTER        │
                   │     (Router0)      │
                   │ Gi0/0   Gi0/1      │
                   └───┬─────────┬─────┘
                       │         │
        ┌──────────────┘         └──────────────┐
        │                                       │
┌───────────────┐                      ┌───────────────┐
│  SWITCH A     │                      │  SWITCH B     │
│  (ACCOUNTS)   │                      │  (DELIVERY)   │
└─────┬─────┬───┘                      └─────┬─────┬───┘
      │     │                                  │     │
  ┌───▼──┐ ┌▼─────┐                      ┌────▼──┐ ┌▼─────┐
  │ PC1  │ │ PC2  │                      │ PC3   │ │ PC4  │
  └──────┘ └──────┘                      └────────┘ └──────┘
      │                                       │
  ┌───▼────┐                            ┌─────▼────┐
  │Printer │                            │ Printer   │
  └────────┘                            └───────────┘

🧮 SUBNETTING DETAILS
Network Given

    192.168.40.0 /24

Subnet Mask Used
    /25  → 255.255.255.128

📊 SUBNET ALLOCATION TABLE
🏢 ACCOUNTS Department
| Parameter       | Value                         |
| --------------- | ----------------------------- |
| Network ID      | 192.168.40.0/25               |
| Subnet Mask     | 255.255.255.128               |
| Host Range      | 192.168.40.1 – 192.168.40.126 |
| Broadcast       | 192.168.40.127                |
| Default Gateway | 192.168.40.1                  |

🚚 DELIVERY Department

| Parameter       | Value                           |
| --------------- | ------------------------------- |
| Network ID      | 192.168.40.128/25               |
| Subnet Mask     | 255.255.255.128                 |
| Host Range      | 192.168.40.129 – 192.168.40.254 |
| Broadcast       | 192.168.40.255                  |
| Default Gateway | 192.168.40.129                  |

🖧 ROUTER CONFIGURATION

enable
configure terminal

interface range gigabitEthernet0/0 - 1
no shutdown
exit

interface gigabitEthernet0/0
ip address 192.168.40.1 255.255.255.128
exit

interface gigabitEthernet0/1
ip address 192.168.40.129 255.255.255.128
exit

💻 HOST IP CONFIGURATION

| Device  | IP Address   | Subnet Mask     | Gateway      |
| ------- | ------------ | --------------- | ------------ |
| PC1     | 192.168.40.2 | 255.255.255.128 | 192.168.40.1 |
| PC2     | 192.168.40.3 | 255.255.255.128 | 192.168.40.1 |
| Printer | 192.168.40.4 | 255.255.255.128 | 192.168.40.1 |

DELIVERY
| Device  | IP Address     | Subnet Mask     | Gateway        |
| ------- | -------------- | --------------- | -------------- |
| PC3     | 192.168.40.130 | 255.255.255.128 | 192.168.40.129 |
| PC4     | 192.168.40.131 | 255.255.255.128 | 192.168.40.129 |
| Printer | 192.168.40.132 | 255.255.255.128 | 192.168.40.129 |

✅ TESTING & VERIFICATION

🇮🇩

    Ping antar PC beda departemen BERHASIL

    Ping PC ke Printer BERHASIL

    Jaringan berfungsi sesuai desain

Eng

    Inter-department ping SUCCESS

    PC to Printer communication SUCCESS

    Network operates as expected

🛠 TECHNOLOGIES IMPLEMENTED

    - Router & Access Layer Switch

    - Proper Network Cabling

    - IP Subnetting

    - Static IP Configuration

    - Router Interface Configuration

    - Network Connectivity Testing