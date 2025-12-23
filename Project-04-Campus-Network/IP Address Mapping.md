# 📌 IP Address Mapping – Campus Network Design

Dokumen ini berisi pemetaan lengkap **IP Address, VLAN, subnet, gateway, dan perangkat** berdasarkan konfigurasi jaringan yang telah dibuat pada proyek **Campus Network Design**.

---

## 🧩 VLAN & IP Addressing Plan

### 🔹 Main Campus – Building A

| Department | VLAN | Network        | Subnet Mask   | Default Gateway | IP Assignment |
| ---------- | ---- | -------------- | ------------- | --------------- | ------------- |
| Admin      | 10   | 192.168.1.0/24 | 255.255.255.0 | 192.168.1.1     | DHCP          |
| HR         | 20   | 192.168.2.0/24 | 255.255.255.0 | 192.168.2.1     | DHCP          |
| Finance    | 30   | 192.168.3.0/24 | 255.255.255.0 | 192.168.3.1     | DHCP          |
| Business   | 40   | 192.168.4.0/24 | 255.255.255.0 | 192.168.4.1     | DHCP          |

---

### 🔹 Main Campus – Building B

| Department              | VLAN | Network        | Subnet Mask   | Default Gateway | IP Assignment |
| ----------------------- | ---- | -------------- | ------------- | --------------- | ------------- |
| Engineering & Computing | 50   | 192.168.5.0/24 | 255.255.255.0 | 192.168.5.1     | DHCP          |
| Arts & Design           | 60   | 192.168.6.0/24 | 255.255.255.0 | 192.168.6.1     | DHCP          |

---

### 🔹 Main Campus – Building C

| Department    | VLAN | Network        | Subnet Mask   | Default Gateway | IP Assignment |
| ------------- | ---- | -------------- | ------------- | --------------- | ------------- |
| Student Labs  | 70   | 192.168.7.0/24 | 255.255.255.0 | 192.168.7.1     | DHCP          |
| IT Department | 80   | 192.168.8.0/24 | 255.255.255.0 | 192.168.8.1     | Static        |

---

### 🔹 Branch Campus

| Department   | VLAN | Network         | Subnet Mask   | Default Gateway | IP Assignment |
| ------------ | ---- | --------------- | ------------- | --------------- | ------------- |
| Staff        | 90   | 192.168.9.0/24  | 255.255.255.0 | 192.168.9.1     | DHCP          |
| Student Labs | 100  | 192.168.10.0/24 | 255.255.255.0 | 192.168.10.1    | DHCP          |

---

## 🌐 WAN / Router IP Mapping

| Link          | Network       | Subnet Mask     | Device        | Interface | IP Address |
| ------------- | ------------- | --------------- | ------------- | --------- | ---------- |
| Main ↔ Branch | 10.10.10.4/30 | 255.255.255.252 | MAIN-ROUTER   | Serial    | 10.10.10.5 |
| Main ↔ Branch | 10.10.10.4/30 | 255.255.255.252 | BRANCH-ROUTER | Serial    | 10.10.10.6 |
| Main ↔ Cloud  | 20.0.0.0/30   | 255.255.255.252 | CLOUD         | Gig0/0    | 20.0.0.1   |

---

## 🖥️ Server IP Address Mapping (Static)

| Server       | Location       | IP Address   | Subnet Mask     | Default Gateway |
| ------------ | -------------- | ------------ | --------------- | --------------- |
| Web Server   | IT Dept (Main) | 192.168.8.10 | 255.255.255.0   | 192.168.8.1     |
| FTP Server   | IT Dept (Main) | 192.168.8.20 | 255.255.255.0   | 192.168.8.1     |
| Email Server | Cloud          | 20.0.0.2     | 255.255.255.252 | 20.0.0.1        |

---

## 🧠 IP Addressing Method Summary

* **LAN Subnet** menggunakan `/24` (254 host) untuk tiap VLAN
* **WAN Link** menggunakan `/30` (2 host) untuk koneksi antar-router
* **Default Gateway** menggunakan IP pertama (`x.x.x.1`)
* **DHCP** digunakan untuk user & student
* **Static IP** digunakan untuk server & perangkat jaringan
