# Perancangan & Implementasi Jaringan Enterprise PT. Nusantara Network - Pekan 9

## 👥 Daftar Anggota Kelompok 5 DMJK Beserta Peran

1. Aditya Laksamana P Butar Butar_10231006 (Security & Documentation Specialist)
2. Ilham Ahmad Fahriji_10231042 (Network Engineer)
3. Muchlis Wahyu Saputra_10231054 (Network Service Specialist)
4. Nazwa Amelia Zahra_10231068 (Network Architect)
---

## 📄 Daftar Isi

1.  [Pendahuluan](#1-pendahuluan)
    * [1.1 Latar Belakang](#11-latar-belakang)
    * [1.2 Tujuan Proyek](#12-tujuan-proyek)
    * [1.3 Ruang Lingkup Proyek](#13-ruang-lingkup-proyek)
2.  [Analisis Kebutuhan Jaringan PT. Nusantara Network](#2-analisis-kebutuhan-jaringan-pt-nusantara-network)
    * [2.1 Struktur Organisasi & Lokasi](#21-struktur-organisasi--lokasi)
    * [2.2 Pembagian Jaringan (VLAN)](#22-pembagian-jaringan-vlan)
    * [2.3 Koneksi Antar Gedung (WAN)](#23-koneksi-antar-gedung-wan)
    * [2.4 Pengaturan Rute (Routing)](#24-pengaturan-rute-routing)
    * [2.5 Akses Internet & Layanan Dasar](#25-akses-internet--layanan-dasar)
    * [2.6 Keamanan Jaringan](#26-keamanan-jaringan)
3.  [Rencana Pengalamatan IP PT. Nusantara Network](#3-rencana-pengalamatan-ip-pt-nusantara-network)
    * [3.1 Tabel Pembagian Alamat IP](#31-tabel-pembagian-alamat-ip)
    * [3.2 Contoh Pembagian Alamat IP di Server Farm](#32-contoh-pembagian-alamat-ip-di-server-farm)
    * [3.3 Catatan Tambahan](#33-catatan-tambahan)
4.  [Jadwal Rencana Kerja (7 Pekan)](#4-jadwal-rencana-kerja-7-pekan)
5.  [Gambaran Awal Desain Jaringan (Sketsa)](#5-gambaran-awal-desain-jaringan-sketsa)
    * [5.1 Gambaran Umum Topologi](#51-gambaran-umum-topologi)
    * [5.2 Komponen Utama di Setiap Lokasi](#52-komponen-utama-di-setiap-lokasi)
    * [5.3 Pembagian Kelompok Jaringan (VLAN)](#53-pembagian-kelompok-jaringan-vlan)
    * [5.4 Perangkat yang digunakan di Cisco Packet Tracer](#54-perangkat-yang-digunakan-di-cisco-packet-tracer)
    * [5.5 Detail Koneksi dan Kabel (Packet Tracer)](#55-detail-koneksi-dan-kabel-packet-tracer)
6.  [Kesimpulan Awal](#6-kesimpulan-awal)
## 1. Pendahuluan

### 1.1 Latar Belakang

Infrastruktur jaringan komputer merupakan tulang punggung operasional bagi sebagian besar organisasi modern. Ketersediaan jaringan yang andal, aman, dan efisien sangat krusial untuk mendukung komunikasi internal, akses data terpusat, kolaborasi antar departemen, serta interaksi dengan dunia luar. Perancangan jaringan yang matang menjadi fondasi utama untuk memastikan kelancaran aliran informasi dan mendukung produktivitas perusahaan secara keseluruhan. Kegagalan dalam merancang jaringan secara tepat dapat mengakibatkan berbagai masalah, mulai dari kinerja yang lambat, kerentanan keamanan, hingga kesulitan dalam pengelolaan dan skalabilitas di masa depan.

Mata kuliah Desain dan Manajemen Jaringan Komputer bertujuan membekali mahasiswa dengan pengetahuan dan keterampilan praktis yang diperlukan untuk merancang, mengimplementasikan, dan mengelola infrastruktur jaringan yang kompleks. Sebagai puncak dari pembelajaran, proyek akhir semester ini dirancang sebagai wadah bagi mahasiswa untuk mengaplikasikan seluruh konsep teori dan praktik yang telah dipelajari ke dalam sebuah studi kasus nyata. Proyek ini menggunakan pendekatan *Project-Based Learning* (PBL) secara berkelompok, mensimulasikan tantangan yang dihadapi oleh para profesional IT dalam membangun solusi jaringan untuk kebutuhan bisnis spesifik, dalam hal ini adalah untuk PT. Nusantara Network.

PT. Nusantara Network, sebagai perusahaan teknologi informasi dengan struktur organisasi yang tersebar di dua lokasi (Kantor Pusat dan Kantor Cabang) serta memiliki beberapa departemen dengan kebutuhan akses yang berbeda, menghadirkan tantangan desain jaringan yang menarik. Perusahaan ini membutuhkan solusi jaringan yang tidak hanya menghubungkan kedua lokasi secara efisien meskipun dengan bandwidth WAN terbatas, tetapi juga mampu melakukan segmentasi jaringan internal (VLAN) untuk keamanan dan manajemen traffic, menyediakan layanan jaringan esensial seperti DHCP, DNS, dan NAT, serta menerapkan kebijakan keamanan melalui ACL dan routing dinamis (OSPF) untuk konektivitas antar gedung. Pemenuhan kebutuhan kompleks ini memerlukan perencanaan awal yang cermat, yang menjadi fokus utama pada tahap awal proyek ini.

### 1.2 Tujuan Proyek

Tujuan dari pengerjaan proyek ini adalah:

1. Merancang infrastruktur jaringan enterprise yang aman, efisien, terukur (scalable), dan mudah dikelola (manageable) untuk PT. Nusantara Network.
2. Mengimplementasikan rancangan jaringan menggunakan perangkat lunak simulasi (Cisco Packet Tracer atau GNS3).
3. Mengkonfigurasi teknologi jaringan kunci, termasuk VLAN, trunking, routing antar-VLAN, routing statis, routing dinamis (OSPF), koneksi WAN, DHCP, DNS, NAT, dan Access Control List (ACL).
4. Melakukan pengujian menyeluruh untuk memvalidasi fungsionalitas dan keamanan jaringan yang telah diimplementasikan.
5. Mendokumentasikan seluruh proses perancangan, implementasi, konfigurasi, dan pengujian secara komprehensif sesuai format yang ditentukan.
6. Memberikan pengalaman praktis kepada mahasiswa dalam menangani proyek jaringan skala kecil hingga menengah, termasuk aspek kerja tim dan manajemen proyek.

### 1.3 Ruang Lingkup Proyek

Ruang lingkup proyek perancangan dan implementasi jaringan untuk PT. Nusantara Network ini mencakup keseluruhan proses desain dan simulasi infrastruktur jaringan yang menghubungkan dua lokasi perusahaan, yaitu Kantor Pusat (Gedung A) dan Kantor Cabang (Gedung B). Fokus utama meliputi perancangan topologi jaringan yang logis dan fisik, perencanaan skema pengalamatan IP termasuk subnetting untuk setiap segmen jaringan, serta implementasi segmentasi jaringan menggunakan VLAN untuk setiap departemen (IT, Keuangan, SDM, Marketing, Operasional) dan Server Farm guna meningkatkan keamanan dan efisiensi manajemen lalu lintas data. Proyek ini juga mencakup konfigurasi routing antar-VLAN, routing statis di dalam gedung, serta routing dinamis menggunakan protokol OSPF untuk memastikan konektivitas yang andal antar kedua gedung melalui link WAN dengan bandwidth terbatas.

Selain itu, ruang lingkup proyek ini mencakup implementasi layanan jaringan esensial seperti DHCP untuk alokasi IP otomatis di setiap VLAN, DNS untuk resolusi nama domain internal dan eksternal, serta konfigurasi NAT pada router di Kantor Pusat untuk memungkinkan akses internet bagi seluruh jaringan internal melalui satu atau beberapa alamat IP publik. Aspek keamanan jaringan menjadi bagian integral, diwujudkan melalui implementasi Access Control List (ACL) untuk membatasi akses antar departemen sesuai dengan kebijakan keamanan yang akan dirumuskan, serta mempertimbangkan mekanisme keamanan dasar lainnya seperti konsep firewall (meskipun konfigurasi firewall spesifik mungkin disederhanakan dalam simulasi). 

Proyek ini juga menyinggung aspek monitoring dan manajemen jaringan terpusat sebagai kebutuhan, meskipun implementasi detail sistem monitoring mungkin terbatas pada fitur yang didukung simulator. Keseluruhan pekerjaan akan dilakukan menggunakan perangkat lunak simulasi (Cisco Packet Tracer), dan tidak mencakup implementasi fisik menggunakan perangkat keras jaringan.

## 2. Analisis Kebutuhan Jaringan PT. Nusantara Network

Dari penjelasan kasus PT. Nusantara Network, kita bisa simpulkan kebutuhan jaringannya sebagai berikut:

### 2.1 Struktur Organisasi & Lokasi

* Perusahaan mempunyai dua kantor: Kantor Pusat (Gedung A) dan Kantor Cabang (Gedung B).
* **Gedung A:** Ada 3 departemen (IT: 40 komputer, Keuangan: 25 komputer, SDM: 20 komputer) dan 1 pusat server (Server Farm: 10 server). Total sekitar 95 komputer + server.
* **Gedung B:** Ada 2 departemen (Marketing: 30 komputer, Operasional: 35 komputer). Total sekitar 65 komputer.
* Perkiraan awal ada sekitar 160 komputer + server. Jumlah ini belum termasuk alat jaringan lain (router, switch) dan kemungkinan penambahan di masa depan.

### 2.2 Pembagian Jaringan (VLAN)

* **Yang Dibutuhkan:** Tiap departemen (IT, Keuangan, SDM, Marketing, Operasional) dan Server Farm harus punya jaringan terpisah (VLAN sendiri).
* **Kenapa Perlu:** Biar lebih aman (data antar departemen terpisah) dan lalu lintas data lebih teratur (mengurangi *broadcast* yang tidak perlu).

### 2.3 Koneksi Antar Gedung (WAN)

* **Yang Dibutuhkan:** Perlu jalur koneksi khusus (Wide Area Network atau WAN) untuk menyambungkan Gedung A dan Gedung B.
* **Tantangan:** Kecepatan (bandwidth) jalur WAN ini terbatas, jadi harus pintar-pintar atur penggunaannya.

### 2.4 Pengaturan Rute (Routing)

* **Antar Gedung:** Perlu pakai cara otomatis (**OSPF**) untuk mengatur jalur data terbaik antara Gedung A dan Gedung B, biar kalau ada perubahan jalur, jaringan bisa menyesuaikan diri.
* **Dalam Gedung:** Perlu pengaturan jalur data antar VLAN di dalam tiap gedung, supaya departemen yang berbeda bisa saling berhubungan kalau memang diizinkan. (Rencananya pakai routing statis untuk ini, dikerjakan di Pekan 12), tetapi untuk memakai static ini masih dalam diskusi kembali. 

### 2.5 Akses Internet & Layanan Dasar

* **NAT (Network Address Translation):** Perlu diatur supaya semua komputer di dalam jaringan bisa internetan bareng-bareng pakai satu atau beberapa alamat IP publik dari penyedia internet (ISP).
* **DHCP (Dynamic Host Configuration Protocol):** Perlu server DHCP untuk kasih alamat IP, subnet mask, gateway, dan alamat DNS secara otomatis ke komputer-komputer di tiap VLAN. Ini bikin pengaturan IP jadi lebih gampang.
* **DNS (Domain Name System):** Perlu server DNS untuk mengubah nama (misal: `server_internal.nusantara.local`) jadi alamat IP yang dimengerti komputer. Server ini harus bisa untuk nama internal dan eksternal (internet).

### 2.6 Keamanan Jaringan

* **ACL (Access Control List):** Perlu dibuat daftar aturan (ACL) untuk membatasi siapa saja yang boleh mengakses bagian jaringan tertentu. Contohnya, departemen mana yang boleh akses server, atau departemen mana yang tidak boleh saling berhubungan langsung. Aturan detailnya perlu dibuat nanti.
* **Firewall (Konsep):** Perlu ada sistem keamanan di perbatasan jaringan (perimeter) untuk melindungi dari ancaman luar. Konsep firewall akan dipertimbangkan.

## 3. Rencana Pengalamatan IP PT. Nusantara Network

Berikut adalah rencana pembagian alamat IP (IP Address) dan Subnet Mask yang diusulkan untuk jaringan PT. Nusantara Network, dibuat berdasarkan kebutuhan yang sudah dianalisis:

### 3.1 Tabel Pembagian Alamat IP

| Lokasi       | Departemen/Fungsi | VLAN ID | Subnet          | Subnet Mask     | Range IP Bisa Dipakai     | Gateway     | Maks Host |
| :----------- | :---------------- | :------ | :-------------- | :-------------- | :------------------------ | :---------- | :-------- |
| **Gedung A** | IT                | 10      | 10.1.10.0/24    | 255.255.255.0   | 10.1.10.1 - 10.1.10.254   | 10.1.10.1   | 254       |
|              | Keuangan          | 20      | 10.1.20.0/24    | 255.255.255.0   | 10.1.20.1 - 10.1.20.254   | 10.1.20.1   | 254       |
|              | SDM               | 30      | 10.1.30.0/24    | 255.255.255.0   | 10.1.30.1 - 10.1.30.254   | 10.1.30.1   | 254       |
|              | Server Farm       | 40      | 10.1.40.0/24    | 255.255.255.0   | 10.1.40.1 - 10.1.40.254   | 10.1.40.1   | 254       |
| **Gedung B** | Marketing         | 50      | 10.2.50.0/24    | 255.255.255.0   | 10.2.50.1 - 10.2.50.254   | 10.2.50.1   | 254       |
|              | Operasional       | 60      | 10.2.60.0/24    | 255.255.255.0   | 10.2.60.1 - 10.2.60.254   | 10.2.60.1   | 254       |
| **WAN** | Link A-B          | -       | 10.254.1.0/30   | 255.255.255.252 | 10.254.1.1 - 10.254.1.2   | -           | 2         |
| **Internet** | NAT Pool (Contoh) | -       | 203.0.113.0/29  | 255.255.255.248 | 203.0.113.1 - 203.0.113.6 | 203.0.113.1 | 6         |

*Catatan: Alamat 203.0.113.0/29 adalah contoh alamat publik yang biasa dipakai untuk dokumentasi.*

### 3.2 Contoh Pembagian Alamat IP di Server Farm

Server-server penting di Server Farm (VLAN 40) akan diberi alamat IP tetap (statis) agar mudah diakses. Berikut contohnya:

| Fungsi Server     | IP Address | Subnet Mask   | Gateway   |
| :---------------- | :--------- | :------------ | :-------- |
| DHCP Server       | 10.1.40.10 | 255.255.255.0 | 10.1.40.1 |
| DNS Server        | 10.1.40.11 | 255.255.255.0 | 10.1.40.1 |
| Web Server        | 10.1.40.12 | 255.255.255.0 | 10.1.40.1 |
| Database Server   | 10.1.40.13 | 255.255.255.0 | 10.1.40.1 |
| File Server       | 10.1.40.14 | 255.255.255.0 | 10.1.40.1 |
| Monitoring Server | 10.1.40.15 | 255.255.255.0 | 10.1.40.1 |
| ... (server lain) | ...        | 255.255.255.0 | 10.1.40.1 |

### 3.3 Catatan Tambahan

* **Pembagian Subnet:**
    * Kita pakai `/24` (artinya ada 254 alamat IP yang bisa dipakai per kelompok) untuk tiap departemen dan server farm. Ini memberi cukup ruang kalau nanti ada penambahan komputer/server.
    * Gedung A pakai pola alamat `10.1.x.0/24`, Gedung B pakai `10.2.x.0/24`.
    * Nomor VLAN ID dipakai sebagai angka ketiga di alamat IP (oktet ketiga) biar gampang diingat dan dikenali.
* **Koneksi WAN:**
    * Pakai `/30` (cuma 2 alamat IP yang bisa dipakai) sangat pas untuk koneksi langsung antar dua router (point-to-point).
* **DHCP:**
    * Nanti server DHCP akan diatur untuk memberi alamat IP otomatis ke komputer di tiap VLAN. Perlu ditentukan rentang alamat mana yang akan dibagikan otomatis. Contoh: Untuk VLAN 10 (IT), alamat yang dibagikan otomatis bisa dari `10.1.10.50` sampai `10.1.10.250`. Alamat di luar rentang itu bisa dipakai untuk server atau alat jaringan lain yang butuh IP tetap.

## 4. Jadwal Rencana Kerja (7 Pekan)

Berikut adalah rencana kerja proyek untuk 7 pekan ke depan, dimulai dari Pekan 9 hingga Pekan 15:

| Pekan | Fokus Utama                           | Tugas Kelompok                                                                                                                               | Hasil Kerja Utama (Deliverable)                                                                                                                                                |
| :---- | :------------------------------------ | :------------------------------------------------------------------------------------------------------------------------------------------- | :----------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **9** | Perencanaan Awal & Desain Kasar       | Analisis kebutuhan, diskusi ide desain awal, pembagian tugas.                                                                                | **Dokumen Perencanaan Proyek:** Berisi analisis kebutuhan, jadwal kerja, gambaran/sketsa desain awal.                                                                          |
| **10**| Desain Detail & Rencana IP            | Finalisasi bentuk jaringan (topologi fisik & logis), rencana detail pembagian IP (subnetting), tentukan alat yang dipakai, rencana detail VLAN. | **Dokumen Desain Jaringan:** Gambar topologi, Tabel alamat IP, Daftar alat, Rencana VLAN, Screenshot awal di Packet Tracer.                                                    |
| **11**| Pembuatan Dasar Jaringan & VLAN       | Buat topologi dasar di Packet Tracer/GNS3, atur VLAN & Trunking, buat routing antar-VLAN.                                                    | **Laporan Implementasi Tahap 1:** File simulasi, Screenshot hasil, Catatan perintah CLI (Switch & Router - VLAN, Trunk, Inter-VLAN), Hasil tes koneksi, Catatan kendala & solusi. |
| **12**| Pengaturan Routing & Koneksi WAN      | Atur routing statis (dalam gedung), terapkan OSPF (antar gedung), buat simulasi koneksi WAN.                                                 | **Laporan Implementasi Tahap 2:** File simulasi, Catatan perintah CLI (Routing Statis & OSPF), Screenshot tabel routing, Hasil tes koneksi antar gedung, Analisis routing.        |
| **13**| Pembuatan Layanan Jaringan            | Atur server DHCP per departemen, buat server DNS internal, atur NAT untuk akses internet.                                                  | **Laporan Implementasi Tahap 3:** File simulasi, Catatan perintah CLI (DHCP, DNS, NAT), Screenshot hasil tes DHCP, DNS, dan NAT.                                                  |
| **14**| Penerapan Keamanan & Pengujian Akhir  | Terapkan aturan ACL sesuai kebijakan, uji semua fitur jaringan, cari & perbaiki masalah (troubleshooting).                                    | **Laporan Implementasi Tahap 4:** File simulasi final, Catatan perintah CLI (ACL), Tabel hasil pengujian & bukti, Laporan perbaikan masalah, Analisis keamanan.                    |
| **15**| Penyelesaian Laporan & Persiapan Demo | Rapikan semua catatan/laporan, siapkan bahan presentasi, buat video demo/tutorial singkat jaringan yang sudah dibuat.                          | **Laporan Akhir Proyek:** Laporan lengkap, Link file simulasi final, Link video demo, Slide presentasi, Kumpulan semua perintah CLI, Refleksi kelompok.                          |

*Catatan: Pekan 16 adalah jadwal presentasi akhir.*

## 5. Gambaran Awal Desain Jaringan (Sketsa)

Berikut adalah gambaran awal (sketsa) dari desain jaringan yang diusulkan untuk PT. Nusantara Network, beserta penjelasannya:

![Gambar Sketsa Jaringan Awal PT. Nusantara Network](Sketsa_Kel5.png)

### 5.1 Gambaran Umum Topologi

* Sketsa ini menunjukkan jaringan untuk dua lokasi utama: **Gedung A (Kantor Pusat)** dan **Gedung B (Kantor Cabang)**.
* Kedua gedung ini terhubung ke jaringan luar (Internet) melalui **ISP** (Penyedia Layanan Internet).
* Gedung A berisi Departemen IT, Keuangan, SDM, dan Server Farm.
* Gedung B berisi Departemen Marketing dan Operasional.

### 5.2 Komponen Utama di Setiap Lokasi

* **Koneksi ke Luar & Antar Gedung (Versi Sketsa):**
    * Dalam sketsa ini, terlihat ada satu **Router Utama** di bagian atas yang menjadi pintu gerbang ke ISP dan juga titik sambungan untuk kedua gedung. Ini adalah penyederhanaan visual untuk tahap awal.
* **Di Dalam Gedung A:**
    * **Pengaturan Jaringan Internal:** Setiap bagian (Departemen IT, Keuangan, SDM, Server Farm) digambarkan sebagai kelompok alat (komputer/server). Garis-garis hubungan di dalamnya menunjukkan adanya **Switch Access** (yang terhubung langsung ke komputer/server) yang kemudian terhubung ke alat pusat di gedung itu. Alat pusat ini, sesuai rencana, adalah **Switch Layer 3** yang tugasnya membagi jaringan pakai VLAN dan mengatur jalur data antar departemen di Gedung A.
    * **Server Farm:** Ini adalah tempat khusus untuk server-server penting (seperti DHCP, DNS, dll.) yang punya VLAN sendiri.
    * **Firewall (Konsep):** Walaupun tidak digambar, idealnya ada **Firewall** (alat atau fitur keamanan) di dekat Router Utama untuk melindungi jaringan dari serangan luar.
* **Di Dalam Gedung B:**
    * **Pengaturan Jaringan Internal:** Sama seperti Gedung A, Departemen Marketing dan Operasional digambarkan sebagai kelompok alat yang terhubung secara bertingkat, menandakan adanya **Switch Access** dan **Switch Layer 3** untuk mengatur VLAN dan jalur data di Gedung B.
    * **Router (Konsep):** Sebenarnya, Gedung B perlu **Router** sendiri (Edge Router) untuk terhubung ke jaringan WAN. Di sketsa ini, koneksinya disederhanakan lewat Router Utama.
* **Koneksi Antar Lokasi (WAN) - Sebenarnya:**
    * Meskipun sketsa menyederhanakannya, implementasi nanti akan memakai **koneksi WAN** (misalnya, jalur sewa khusus atau teknologi lain) yang menghubungkan langsung Router di Gedung A dan Router di Gedung B.
    * Protokol **OSPF** akan dipakai di koneksi WAN ini agar router bisa saling bertukar informasi jalur terbaik secara otomatis.

### 5.3 Pembagian Kelompok Jaringan (VLAN)

Jaringan akan dibagi menjadi kelompok-kelompok (VLAN) berikut:

* **VLAN 10:** Departemen IT (Gedung A)
* **VLAN 20:** Departemen Keuangan (Gedung A)
* **VLAN 30:** Departemen SDM (Gedung A)
* **VLAN 40:** Server Farm (Gedung A)
* **VLAN 50:** Departemen Marketing (Gedung B)
* **VLAN 60:** Departemen Operasional (Gedung B)

### 5.4 Perangkat yang digunakan di Cisco Packet Tracer

Berikut adalah beberapa jenis perangkat yang umum digunakan dalam Cisco Packet Tracer dan cocok untuk desain ini:

* **Router:** Satu router di setiap gedung (misal, Router Core di Gedung A dan Router Edge di Gedung B) untuk menangani koneksi WAN, menjalankan OSPF, dan melakukan NAT (di Gedung A).
    * Contoh Model yang cocok di Packet Tracer yaitu menggunakan Cisco ISR **2911** atau **4321**. Model ini cukup kuat untuk routing, NAT, dan OSPF. Mungkin perlu menambahkan modul serial (misal, HWIC-2T) untuk simulasi koneksi WAN point-to-point.
* **Switch Layer 3 (Multilayer Switch):** Ini akan ditempatkan di pusat jaringan setiap gedung untuk menghubungkan berbagai Switch Access dan melakukan routing antar-VLAN. Ini lebih efisien daripada melewatkan semua trafik antar-VLAN ke router.
    * Contoh Model yang cocok di Packet Tracer yaitu menggunakan Cisco Catalyst **3560** atau **3650**. Keduanya mendukung routing antar-VLAN.
* **Switch Access (Layer 2 Switch):** Digunakan di setiap lantai atau area departemen untuk menghubungkan komputer pengguna, printer, dan perangkat lain ke jaringan dan menempatkannya di VLAN yang sesuai.
    * Contoh Model yang cocok di Packet Tracer yaitu menggunakan Cisco Catalyst **2960**. Ini adalah switch Layer 2 standar yang banyak digunakan.
* **Firewall (Opsional tapi disarankan):** Untuk keamanan tambahan di perimeter jaringan (antara router utama dan internet/jaringan internal).
    * Contoh Model yang cocok di Packet Tracer yaitu menggunakan Cisco **ASA 5506-X**. Ini adalah firewall yang bisa dikonfigurasi untuk aturan keamanan dasar.
* **Server:** Untuk menjalankan layanan seperti DHCP, DNS, Web Server, dll.
    * Contoh Model yang cocok di Packet Tracer yaitu menggunakan perangkat **Server-PT** generik yang tersedia dan konfigurasikan layanannya sesuai kebutuhan (DHCP, DNS, HTTP, dll.).

*Catatan: Pemilihan model spesifik ini adalah pikiran awal kami. Jumlah pasti dan model dapat disesuaikan lebih lanjut pada tahap desain detail nantinya di pekan ke 10 berdasarkan analisis performa dan fitur yang lebih mendalam.*

### 5.5 Detail Koneksi dan Kabel (Packet Tracer)

Berikut adalah penghubungan antara perangkat perangkat di atas yang akan cocok menggunakan Cisco Packet Tracer:

* **Router Gedung A <--> Router Gedung B (Koneksi WAN):**
    * **Kabel:** Gunakan kabel **Serial DCE/DTE**. Pilih salah satu router sebagai DCE (yang mengatur *clock rate*) dan hubungkan ke router lain sebagai DTE.
    * **Port:** Sambungkan port Serial (misal, `Serial0/0/0` dari modul HWIC-2T) di Router A ke port Serial (misal, `Serial0/0/0`) di Router B.
* **Router Gedung A <--> ISP Cloud:**
    * **Kabel:** Gunakan kabel **Copper Straight-Through** (kabel LAN lurus standar).
    * **Port:** Sambungkan port GigabitEthernet (misal, `GigabitEthernet0/0`) di Router A ke port Ethernet yang sesuai di Cloud-PT. *(Jika Anda menambahkan Firewall ASA 5506-X, sambungkan port `GigabitEthernet0/0` Router A ke port `GigabitEthernet1/2` (inside) Firewall, lalu sambungkan port `GigabitEthernet1/1` (outside) Firewall ke Cloud-PT)*.
* **Router Gedung A <--> Switch Layer 3 Gedung A:**
    * **Kabel:** Gunakan kabel **Copper Straight-Through**.
    * **Port:** Sambungkan port GigabitEthernet (misal, `GigabitEthernet0/1`) di Router A ke salah satu port GigabitEthernet (misal, `GigabitEthernet1/0/1`) di Switch Layer 3 Gedung A.
* **Router Gedung B <--> Switch Layer 3 Gedung B:**
    * **Kabel:** Gunakan kabel **Copper Straight-Through**.
    * **Port:** Sambungkan port GigabitEthernet (misal, `GigabitEthernet0/1`) di Router B ke salah satu port GigabitEthernet (misal, `GigabitEthernet1/0/1`) di Switch Layer 3 Gedung B.
* **Switch Layer 3 <--> Switch Access (di tiap Gedung):**
    * **Kabel:** Gunakan kabel **Copper Cross-Over**. Sebaiknya pakai port GigabitEthernet di kedua ujung jika memungkinkan untuk kecepatan maksimal antar switch.
    * **Port:** Sambungkan beberapa port GigabitEthernet (misal, `GigabitEthernet1/0/2`, `1/0/3`, dst.) di Switch Layer 3 ke port GigabitEthernet (misal, `GigabitEthernet0/1` atau `0/2`) di masing-masing Switch Access.
    * **Penting:** Port-port ini harus dikonfigurasi sebagai **Trunk** agar bisa dilewati data dari berbagai VLAN.
* **Switch Access <--> Komputer Klien / Server:**
    * **Kabel:** Gunakan kabel **Copper Straight-Through**.
    * **Port:** Sambungkan port FastEthernet (misal, `FastEthernet0/1` sampai `FastEthernet0/24`) di Switch Access ke port FastEthernet di Komputer (PC-PT) atau Server (Server-PT).
    * **Penting:** Port-port di Switch Access ini harus dikonfigurasi sebagai **Access Port** dan dimasukkan ke **VLAN yang benar** sesuai departemen atau fungsinya (misal, PC di Dept IT masuk VLAN 10, Server DHCP masuk VLAN 40).

## 6. Kesimpulan Awal

Berdasarkan analisis awal kebutuhan PT. Nusantara Network, desain jaringan yang kami usulkan akan mengadopsi pendekatan hierarkis dengan segmentasi VLAN yang jelas untuk meningkatkan keamanan dan manajemen. Konektivitas antar gedung akan dioptimalkan dengan routing dinamis (OSPF) untuk adaptasi otomatis terhadap perubahan topologi jaringan.

Pada tahap berikutnya, tim akan fokus pada detil perencanaan IP addressing dan subnetting untuk memastikan pemanfaatan alamat IP yang efisien dan skalabel. Kami juga akan menentukan spesifikasi perangkat yang dibutuhkan serta menyusun konfigurasi dasar untuk implementasi awal.

