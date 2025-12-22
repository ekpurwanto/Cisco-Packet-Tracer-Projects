🇮🇩 DESKRIPSI PROYEK

Proyek ini merupakan implementasi jaringan cabang (branch network) untuk XYZ Company, sebuah perusahaan yang sedang berkembang pesat.
Jaringan cabang beroperasi terpisah dari HQ, menggunakan 1 router dan 1 switch Cisco, serta menerapkan:

    - VLAN

    - Inter-VLAN Routing

    - DHCP Server

    - Wireless Network (Wi-Fi)

Setiap departemen berada pada VLAN berbeda, namun tetap dapat saling berkomunikasi.

🇬🇧 PROJECT DESCRIPTION

This project implements a branch office network for XYZ Company, a fast-growing organization.
The branch network operates independently from HQ, using one Cisco router and one Cisco switch, and implements:

   - VLAN

   - Inter-VLAN Routing

   - DHCP Server

   - Wireless Networking

Each department is placed in a different VLAN, while maintaining full inter-department communication.

📌 CASE STUDY REQUIREMENTS
🇮🇩 Kebutuhan
- 1 Router & 1 Switch (Cisco)

- 3 Departemen:

    - Admin / IT

    - Finance / HR

    - Customer Service / Reception

- Setiap departemen:

    - VLAN berbeda

    - Wireless Network

- IP Address otomatis (DHCP)

- Semua VLAN saling berkomunikasi

- Base Network dari ISP: 192.168.1.0

🇬🇧 Requirements

- 1 Router & 1 Switch (Cisco)

- 3 Departments:

    - Admin / IT

    - Finance / HR

    - Customer Service / Reception

Each department:

    - Different VLAN

    - Wireless access

- Automatic IP assignment (DHCP)

- Inter-VLAN communication

- ISP Base Network: 192.168.1.0

🏗️ NETWORK TOPOLOGY (ASCII DIAGRAM)

                     ┌──────────────────┐
                     │      ROUTER      │
                     │   (Router0)      │
                     │   Gi0/0 (Trunk)  │
                     └────────┬─────────┘
                              │
                        ┌─────▼─────┐
                        │   SWITCH   │
                        │  (2960)    │
                        └─┬────┬────┬┘
          VLAN 10 ────────┘    │    └──────── VLAN 30
                               │
                          VLAN 20

   ┌─────────────────┐   ┌─────────────────┐   ┌────────────────────────┐
   │ ADMIN / IT       │   │ FINANCE / HR    │   │ CUSTOMER SERVICE        │
   │ VLAN 10          │   │ VLAN 20         │   │ VLAN 30                 │
   │ PC + Printer     │   │ PC + Printer    │   │ PC + Printer            │
   │ Access Point     │   │ Access Point    │   │ Access Point            │
   └─────────────────┘   └─────────────────┘   └────────────────────────┘
🧮 SUBNETTING SUMMARY
Base Network
    192.168.1.0 /24

Required Subnets
    3 Subnets → 2² = 4 (Borrow 2 bits)

Subnet Mask
    /26 → 255.255.255.192


📊 SUBNET ALLOCATION TABLE

| VLAN | Department       | Network ID       | Host Range  | Broadcast | Gateway       |
| ---- | ---------------- | ---------------- | ----------- | --------- | ------------- |
| 10   | Admin / IT       | 192.168.1.0/26   | .1 – .62    | .63       | 192.168.1.1   |
| 20   | Finance / HR     | 192.168.1.64/26  | .65 – .126  | .127      | 192.168.1.65  |
| 30   | Customer Service | 192.168.1.128/26 | .129 – .190 | .191      | 192.168.1.129 |


🔀 VLAN CONFIGURATION (SWITCH)

    enable
    configure terminal

    vlan 10
    name ADMIN_IT

    vlan 20
    name FINANCE_HR

    vlan 30
    name CUSTOMER_SERVICE

Assign Ports to VLANs
    interface range fa0/2 - 4
    switchport mode access
    switchport access vlan 10

    interface range fa0/5 - 7
    switchport mode access
    switchport access vlan 20

    interface range fa0/8 - 10
    switchport mode access
    switchport access vlan 30

🔁 INTER-VLAN ROUTING (Router-on-a-Stick)
    interface gigabitEthernet0/0
    no shutdown

    VLAN 10
        interface gigabitEthernet0/0.10
        encapsulation dot1Q 10
        ip address 192.168.1.1 255.255.255.192
    
    VLAN 20
        interface gigabitEthernet0/0.20
        encapsulation dot1Q 20
        ip address 192.168.1.65 255.255.255.192

    VLAN 30
        interface gigabitEthernet0/0.30
        encapsulation dot1Q 30
        ip address 192.168.1.129 255.255.255.192

📡 DHCP SERVER CONFIGURATION (Router)
    VLAN 10
        ip dhcp pool ADMIN
        network 192.168.1.0 255.255.255.192
        default-router 192.168.1.1
        dns-server 192.168.1.1
        domain-name admin.local

    VLAN 20
        ip dhcp pool FINANCE
        network 192.168.1.64 255.255.255.192
        default-router 192.168.1.65
        dns-server 192.168.1.65
        domain-name finance.local

    VLAN 30
        ip dhcp pool CS
        network 192.168.1.128 255.255.255.192
        default-router 192.168.1.129
        dns-server 192.168.1.129
        domain-name cs.local

📶 WIRELESS CONFIGURATION
| Department       | SSID         | Security | Password      |
| ---------------- | ------------ | -------- | ------------- |
| Admin / IT       | ADMIN-WIFI   | WPA2-PSK | Admin@1234    |
| Finance / HR     | FINANCE-WIFI | WPA2-PSK | Finance@1234  |
| Customer Service | CS-WIFI      | WPA2-PSK | Customer@1234 |

✅ TESTING & VERIFICATION
🇮🇩
- DHCP berhasil memberikan IP otomatis

- Perangkat wireless berhasil terhubung

- Ping antar VLAN berhasil

- Inter-VLAN Routing berfungsi

🇬🇧

- DHCP successfully assigns IP addresses

- Wireless clients connect successfully

- Inter-VLAN ping successful

- Full network connectivity verified

🛠 TECHNOLOGIES IMPLEMENTED

    - VLAN

    - Inter-VLAN Routing

    - DHCP Server

    - Wireless Access Point

    - Subnetting

    - Router-on-a-Stick

    - Cisco Packet Tracer






