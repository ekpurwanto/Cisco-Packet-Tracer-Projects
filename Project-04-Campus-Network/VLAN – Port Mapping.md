# 📌 VLAN – Port Mapping

Dokumen ini berisi pemetaan **VLAN ke Switch dan Port** berdasarkan konfigurasi aktual pada proyek **Campus Network Design**. File ini melengkapi `IP-Address-Mapping.md` dan digunakan untuk troubleshooting serta dokumentasi teknis.

---

## 🔹 Main Campus – Core & Distribution

### MAIN-SWITCH-L3

| Port    | Mode   | VLAN  | Terhubung ke        |
| ------- | ------ | ----- | ------------------- |
| Gi1/0/1 | Trunk  | 10–80 | MAIN-ROUTER         |
| Gi1/0/2 | Access | 10    | SW-A-ADMIN          |
| Gi1/0/3 | Access | 20    | SW-A-HR             |
| Gi1/0/4 | Access | 30    | SW-A-FINANCE        |
| Gi1/0/5 | Access | 40    | SW-A-BUSSINESS      |
| Gi1/0/6 | Access | 50    | SW-B-E&C            |
| Gi1/0/7 | Access | 60    | SW-B-A&D            |
| Gi1/0/8 | Access | 70    | SW-C-LAB-STUDENT    |
| Gi1/0/9 | Access | 80    | IT / Server Segment |

---

## 🔹 Main Campus – Access Switches

### SW-A-ADMIN (VLAN 10)

| Port Range | Mode   | VLAN | Device    |
| ---------- | ------ | ---- | --------- |
| Fa0/1–24   | Access | 10   | Admin PCs |

### SW-A-HR (VLAN 20)

| Port Range | Mode   | VLAN | Device |
| ---------- | ------ | ---- | ------ |
| Fa0/1–24   | Access | 20   | HR PCs |

### SW-A-FINANCE (VLAN 30)

| Port Range | Mode   | VLAN | Device      |
| ---------- | ------ | ---- | ----------- |
| Fa0/1–24   | Access | 30   | Finance PCs |

### SW-A-BUSSINESS (VLAN 40)

| Port Range | Mode   | VLAN | Device       |
| ---------- | ------ | ---- | ------------ |
| Fa0/1–24   | Access | 40   | Business PCs |

---

## 🔹 Main Campus – Building B & C

### SW-B-E&C (VLAN 50)

| Port Range | Mode   | VLAN | Device                      |
| ---------- | ------ | ---- | --------------------------- |
| Fa0/1–24   | Access | 50   | Engineering & Computing Lab |

### SW-B-A&D (VLAN 60)

| Port Range | Mode   | VLAN | Device            |
| ---------- | ------ | ---- | ----------------- |
| Fa0/1–24   | Access | 60   | Arts & Design Lab |

### SW-C-LAB-STUDENT (VLAN 70)

| Port Range | Mode   | VLAN | Device      |
| ---------- | ------ | ---- | ----------- |
| Fa0/1–24   | Access | 70   | Student Lab |

---

## 🔹 Branch Campus – Distribution & Access

### BRANCH-SW-L3

| Port    | Mode   | VLAN   | Terhubung ke          |
| ------- | ------ | ------ | --------------------- |
| Gi1/0/1 | Trunk  | 90,100 | BRANCH-ROUTER         |
| Gi1/0/2 | Access | 90     | SW-BRANCH-STAFF       |
| Gi1/0/3 | Access | 100    | SW-BRANCH-STUDENT-LAB |

---

### SW-BRANCH-STAFF (VLAN 90)

| Port Range | Mode   | VLAN | Device           |
| ---------- | ------ | ---- | ---------------- |
| Fa0/1–24   | Access | 90   | Branch Staff PCs |

### SW-BRANCH-STUDENT-LAB (VLAN 100)

| Port Range | Mode   | VLAN | Device             |
| ---------- | ------ | ---- | ------------------ |
| Fa0/1–24   | Access | 100  | Branch Student Lab |

---

## 🧠 Catatan Desain

* **Access Port** → hanya membawa 1 VLAN
* **Trunk Port** → membawa banyak VLAN (802.1Q)
* Semua port access disesuaikan dengan fungsi departemen
* Mapping ini mempermudah troubleshooting (VLAN mismatch, wrong port, dll.)

---
