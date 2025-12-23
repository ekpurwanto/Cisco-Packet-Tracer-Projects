1️⃣ Verifikasi VLAN (Layer 2)
Perintah
show vlan brief

Hasil yang Diharapkan
VLAN	Nama	Status	Keterangan
10	ADMIN	Active	Building A
20	HR	Active	Building A
30	FINANCE	Active	Building A
40	BUSINESS	Active	Building A
50	ENG-COMP	Active	Building B
60	ART-DESIGN	Active	Building B
70	STUDENT-LAB	Active	Building C
80	IT	Active	Building C
90	BRANCH-STAFF	Active	Branch
100	BRANCH-LAB	Active	Branch
2️⃣ Verifikasi Trunk Link
Perintah
show interfaces trunk

Checklist

✔ Mode: trunk

✔ Allowed VLANs: 10–100

✔ Trunk aktif antara:

MAIN-SWITCH-L3 ↔ Access Switch

BRANCH-SW-L3 ↔ Access Switch

3️⃣ Verifikasi Routing (Layer 3)
Perintah
show ip route

Routing Table Harus Menampilkan:
Code	Arti
C	Connected Network
R	RIP v2 Learned Route

Contoh route valid:

R 192.168.9.0/24 via 10.10.10.6
R 192.168.1.0/24 via 10.10.10.5

4️⃣ Verifikasi RIP v2
Perintah
show ip protocols

Checklist

✔ Routing Protocol: RIP

✔ Version: 2

✔ Networks:

10.10.10.4/30

20.0.0.0/30

5️⃣ Verifikasi Konektivitas (Ping Test)
Test Antar VLAN (Inter-VLAN)
ping 192.168.3.10
ping 192.168.6.10


✔ Reply = sukses inter-VLAN routing

Test Main ↔ Branch
ping 192.168.9.10
ping 10.10.10.10


✔ Reply = RIP berfungsi

Test ke Cloud / Email Server
ping 20.0.0.2


✔ Reply = WAN & static routing OK

6️⃣ Kesimpulan Verifikasi

✅ VLAN aktif
✅ Trunk berfungsi
✅ Inter-VLAN routing sukses
✅ RIP v2 berjalan normal
✅ Server Cloud dapat diakses
