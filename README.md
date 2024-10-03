# Write Up-Jarkom-Modul-2-Kelompok-IT33

| Nama | NRP |
|----------|----------|
| Ricko Mianto Jaya Saputra | 5027231031 |
| Tsaldia Hukma Cita | 5027231036 | 

# Daftar Isi
1. [Topology](#topology)
2. [Konfigurasi](#konfigurasi)
3. [Soal](#soal)
   - [No 1](#1)
   - [No 2](#2)
   - [No 3](#3)
   - [No 4](#4)
   - [No 5](#5)
   - [No 6](#6)
   - [No 7](#7)
   - [No 8](#8)
   - [No 9](#9)
   - [No 10](#10)
   - [No 11](#11)
   - [No 12](#12)
   - [No 13](#13)
   - [No 14](#14)
   - [No 15](#15)
   - [No 16](#16)
   - [No 17](#17)
   - [No 18](#18)
   - [No 19](#19)
   - [No 20](#20)

## TOPOLOGY
Sebuah kerajaan besar di Indonesia sedang mengalami pertempuran dengan penjajah. Kerajaan tersebut adalah Sriwijaya. Karena merasa terdesak Sriwijaya meminta bantuan pada Majapahit untuk mempertahankan wilayahnya. Pertempuran besar tersebut berada di Nusantara. Untuk topologi lihat pada link [ini](https://drive.google.com/drive/folders/14Pe2HOks3NzF4f_mNdrziIF56QwiKfFn).
- Kelompok IT33 mendapatkan topologi 3
![image](https://github.com/user-attachments/assets/d4dedbb8-89cb-4d44-89ae-63f696348bb5)

## KONFIGURASI
| Kelompok | Prefix IP |
|----------|----------|
| IT33 | 192.233 |

**Nusantara**
 auto eth0
 iface eth0 inet dhcp

 auto eth1
 iface eth1 inet static
 	address 192.233.1.1
 	netmask 255.255.255.0

 auto eth2
 iface eth2 inet static
 	address 192.233.2.1
 	netmask 255.255.255.0

**Majapahit**
auto eth0
iface eth0 inet static
	address 192.233.1.2
	netmask 255.255.255.0
   gateway 192.233.1.1

**Mulawarman**
auto eth0
iface eth0 inet static
	address 192.233.1.3
	netmask 255.255.255.0
   gateway 192.233.1.1
   
**GrahamBell**
auto eth0
iface eth0 inet static
	address 192.233.1.4
	netmask 255.255.255.0
   gateway 192.233.1.1
   
**Samaratungga**
auto eth0
iface eth0 inet static
	address 192.233.1.5
	netmask 255.255.255.0
   gateway 192.233.1.1

**Solok**
auto eth0
iface eth0 inet static
	address 192.233.2.2
	netmask 255.255.255.0
   gateway 192.233.2.1
   
**Srikandi**
auto eth0
iface eth0 inet static
	address 192.233.2.3
	netmask 255.255.255.0
   gateway 192.233.2.1

**Kotalingga**
auto eth0
iface eth0 inet static
	address 192.233.2.4
	netmask 255.255.255.0
   gateway 192.233.2.1
   
**Bedahulu**
auto eth0
iface eth0 inet static
	address 192.233.2.5
	netmask 255.255.255.0
   gateway 192.233.2.1
   
**Tanjungkulai**
auto eth0
iface eth0 inet static
	address 192.233.2.6
	netmask 255.255.255.0
   gateway 192.233.2.1
   
**Sriwijaya**
auto eth0
iface eth0 inet static
	address 192.233.2.7
	netmask 255.255.255.0
   gateway 192.233.2.1


## SOAL 
### 1
Untuk mempersiapkan peperangan World War MMXXIV (Iya sebanyak itu), Sriwijaya membuat dua kotanya menjadi web server yaitu Tanjungkulai, dan Bedahulu, serta Sriwijaya sendiri akan menjadi DNS Master. Kemudian karena merasa terdesak, Majapahit memberikan bantuan dan menjadikan kerajaannya (Majapahit) menjadi DNS Slave. 

- Buka terminal Nusantara, masukkan command `nano /root/.bashrc` --> masukkan `iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.233.0.0/16` ini menggunakan prefix IP kelompok 

### 2
Karena para pasukan membutuhkan koordinasi untuk melancarkan serangannya, maka buatlah sebuah domain yang mengarah ke Solok dengan alamat sudarsana.xxxx.com dengan alias www.sudarsana.xxxx.com, dimana xxxx merupakan kode kelompok. Contoh: sudarsana.it01.com.


### 3
Para pasukan juga perlu mengetahui mana titik yang akan diserang, sehingga dibutuhkan domain lain yaitu pasopati.xxxx.com dengan alias www.pasopati.xxxx.com yang mengarah ke Kotalingga.

### 4
Markas pusat meminta dibuatnya domain khusus untuk menaruh informasi persenjataan dan suplai yang tersebar. Informasi dan suplai meme terbaru tersebut mengarah ke Tanjungkulai dan domain yang ingin digunakan adalah rujapala.xxxx.com dengan alias www.rujapala.xxxx.com.

### 5
Pastikan domain-domain tersebut dapat diakses oleh seluruh komputer (client) yang berada di Nusantara.

### 6
Beberapa daerah memiliki keterbatasan yang menyebabkan hanya dapat mengakses domain secara langsung melalui alamat IP domain tersebut. Karena daerah tersebut tidak diketahui secara spesifik, pastikan semua komputer (client) dapat mengakses domain pasopati.xxxx.com melalui alamat IP Kotalingga (Notes: menggunakan pointer record).

### 7
Akhir-akhir ini seringkali terjadi serangan brainrot ke DNS Server Utama, sebagai tindakan antisipasi kamu diperintahkan untuk membuat DNS Slave di Majapahit untuk semua domain yang sudah dibuat sebelumnya yang mengarah ke Sriwijaya.

### 8
Kamu juga diperintahkan untuk membuat subdomain khusus melacak kekuatan tersembunyi di Ohio dengan subdomain cakra.sudarsana.xxxx.com yang mengarah ke Bedahulu.

### 9
Karena terjadi serangan DDOS oleh shikanoko nokonoko koshitantan (NUN), sehingga sistem komunikasinya terhalang. Untuk melindungi warga, kita diperlukan untuk membuat sistem peringatan dari siren man oleh Frekuensi Freak dan memasukkannya ke subdomain panah.pasopati.xxxx.com dalam folder panah dan pastikan dapat diakses secara mudah dengan menambahkan alias www.panah.pasopati.xxxx.com dan mendelegasikan subdomain tersebut ke Majapahit dengan alamat IP menuju radar di Kotalingga.

### 10
Markas juga meminta catatan kapan saja meme brain rot akan dijatuhkan, maka buatlah subdomain baru di subdomain panah yaitu log.panah.pasopati.xxxx.com serta aliasnya www.log.panah.pasopati.xxxx.com yang juga mengarah ke Kotalingga.

### 11
Setelah pertempuran mereda, warga IT dapat kembali mengakses jaringan luar dan menikmati meme brainrot terbaru, tetapi hanya warga Majapahit saja yang dapat mengakses jaringan luar secara langsung. Buatlah konfigurasi agar warga IT yang berada diluar Majapahit dapat mengakses jaringan luar melalui DNS Server Majapahit.

### 12
Karena pusat ingin sebuah laman web yang ingin digunakan untuk memantau kondisi kota lainnya maka deploy laman web ini (cek resource yg lb) pada Kotalingga menggunakan apache.

### 13
Karena pusat ingin sebuah laman web yang ingin digunakan untuk memantau kondisi kota lainnya maka deploy laman web ini (cek resource yg lb) pada Kotalingga menggunakan apache.

### 14
Selama melakukan penjarahan mereka melihat bagaimana web server luar negeri, hal ini membuat mereka iri, dengki, sirik dan ingin flexing sehingga meminta agar web server dan load balancer nya diubah menjadi nginx.

### 15
Markas pusat meminta laporan hasil benchmark dengan menggunakan apache benchmark dari load balancer dengan 2 web server yang berbeda tersebut dan meminta secara detail dengan ketentuan:
Nama Algoritma Load Balancer
Report hasil testing apache benchmark 
Grafik request per second untuk masing masing algoritma. 
Analisis
Meme terbaik kalian (terserah ( ͡° ͜ʖ ͡°)) 🤓

### 16
Karena dirasa kurang aman dari brainrot karena masih memakai IP, markas ingin akses ke Solok memakai solok.xxxx.com dengan alias www.solok.xxxx.com (sesuai web server terbaik hasil analisis kalian).

### 17
Agar aman, buatlah konfigurasi agar solok.xxx.com hanya dapat diakses melalui port sebesar π x 10^4 = (phi nya desimal) dan 2000 + 2000 log 10 (10) +700 - π = ?.

### 18
Apa bila ada yang mencoba mengakses IP solok akan secara otomatis dialihkan ke www.solok.xxxx.com.

### 19
Karena probset sudah kehabisan ide masuk ke salah satu worker buatkan akses direktori listing yang mengarah ke resource worker2.

### 20
Worker tersebut harus dapat di akses dengan sekiantterimakasih.xxxx.com dengan alias www.sekiantterimakasih.xxxx.com.
