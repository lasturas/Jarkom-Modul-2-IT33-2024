# Write Up-Jarkom-Modul-2-Kelompok-IT33

| Nama | NRP |
|----------|----------|
| Ricko Mianto Jaya Saputra | 5027231031 |
| Tsaldia Hukma Cita | 5027231036 | 

# Daftar Isi
1. [Topology](#topology)
2. [Konfigurasi](#konfigurasi-ip-address)
3. [Soal](#soal-praktikum)
   - [No 1](#no-1)
   - [No 2](#no-2)
   - [No 3](#no-3)
   - [No 4](#no-4)
   - [No 5](#no-5)
   - [No 6](#no-6)
   - [No 7](#no-7)
   - [No 8](#no-8)
   - [No 9](#no-9)
   - [No 10](#no-10)
   - [No 11](#no-11)
   - [No 12](#no-12)
   - [No 13](#no-13)
   - [No 14](#no-14)
   - [No 15](#no-15)
   - [No 16](#no-16)
   - [No 17](#no-17)
   - [No 18](#no-18)
   - [No 19](#no-19)
   - [No 20](#no-20)

# Topology
Sebuah kerajaan besar di Indonesia sedang mengalami pertempuran dengan penjajah. Kerajaan tersebut adalah Sriwijaya. Karena merasa terdesak Sriwijaya meminta bantuan pada Majapahit untuk mempertahankan wilayahnya. Pertempuran besar tersebut berada di Nusantara. Untuk topologi lihat pada link [ini](https://drive.google.com/drive/folders/14Pe2HOks3NzF4f_mNdrziIF56QwiKfFn).
- Kelompok IT33 mendapatkan topologi 3
![image](https://github.com/user-attachments/assets/d4dedbb8-89cb-4d44-89ae-63f696348bb5)

# Konfigurasi IP Address
| Kelompok | Prefix IP |
|----------|----------|
| IT33 | 192.233 |

| Nama Kota    | Interface | IP Address  | Gateway    |
|--------------|-----------|-------------|------------|
| Nusantara    | eth1      | 192.233.1.1   |            |
|              | eth2      | 192.233.2.1   |            |
| Sriwijaya    | eth0      | 192.233.2.7   | 192.233.2.1  |
| Tanjungkulai | eth0      | 192.233.2.6   | 192.233.2.1  |
| Bedahulu     | eth0      | 192.233.2.5   | 192.233.2.1  |
| Kotalingga   | eth0      | 192.233.2.4   | 192.233.2.1  |
| Srikandi     | eth0      | 192.233.2.3   | 192.233.2.1  |
| Solok        | eth0      | 192.233.2.2   | 192.233.2.1  |
| Majapahit    | eth0      | 192.233.1.2   | 192.233.1.1  |
| Mulawarman   | eth0      | 192.233.1.3   | 192.233.1.1  |
| GrahamBell   | eth0      | 192.233.1.4   | 192.233.1.1  |
| Samaratungga | eth0      | 192.233.1.5   | 192.233.1.1  |

**Nusantara (Router)**  
```
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
```

**Majapahit (DNS Slave)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.1.2   
	netmask 255.255.255.0   
   	gateway 192.233.1.1   
```

**Mulawarman (Client)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.1.3  
	netmask 255.255.255.0  
   	gateway 192.233.1.1  
```
   
**GrahamBell (Client)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.1.4  
	netmask 255.255.255.0  
   	gateway 192.233.1.1  
```
   
**Samaratungga (Client)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.1.5  
	netmask 255.255.255.0  
   	gateway 192.233.1.1  
```

**Solok (Load Balancer)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.2.2  
	netmask 255.255.255.0  
   	gateway 192.233.2.1  
```
   
**Srikandi (Client)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.2.3  
	netmask 255.255.255.0  
  	gateway 192.233.2.1  
```

**Kotalingga (Web Server)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.2.4  
	netmask 255.255.255.0  
   	gateway 192.233.2.1  
```
   
**Bedahulu (Web Servevr)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.2.5  
	netmask 255.255.255.0  
    	gateway 192.233.2.1  
```
   
**Tanjungkulai (Web Server)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.2.6  
	netmask 255.255.255.0  
   	gateway 192.233.2.1  
```
   
**Sriwijaya (DNS Master)**  
```
auto eth0  
iface eth0 inet static  
	address 192.233.2.7  
	netmask 255.255.255.0  
   	gateway 192.233.2.1  
```


# Soal Praktikum 
## No 1

> Untuk mempersiapkan peperangan World War MMXXIV (Iya sebanyak itu), Sriwijaya membuat dua kotanya menjadi web server yaitu Tanjungkulai, dan Bedahulu, serta Sriwijaya sendiri akan menjadi DNS Master. Kemudian karena merasa terdesak, Majapahit memberikan bantuan dan menjadikan kerajaannya (Majapahit) menjadi DNS Slave. 

- Node Master --> Sriwijaya
- Node Slave --> Majapahit
- Node Client --> Mulawarman, GrahamBell, Samaratungga, Srikandi
- Node Web Server --> Kotalingga, Bedahulu, Tanjungkulai
- Node Load Balancer --> Solok

Buka terminal Nusantara, masukkan command untuk masuk ke bash `nano /root/.bashrc` dan inputkan kode berikut untuk NAT dengan menggunakan prefix IP kelompok
```
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.233.0.0/16
``` 

Cek nameserver dengan command berikut pada terminal Nusantara
```
cat /etc/resolv.conf
```
Lalu akan muncul informasi nameserver Nusantara `nameserver 192.168.122.1`

Selanjutnya kita buka terminal setiap node dan masuk ke bash dengan `nano /root/.bashrc`, untuk 
- Node client akan menggunakan 3 IP (rooter, IP master, IP slave)
```
echo 'nameserver 192.168.122.1
nameserver 192.233.2.7
nameserver 192.233.1.2' > /etc/resolv.conf
```
- Node master akan menggunakan IP rooter dan install bind9
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install bind9 -y
```
- Node slave akan menggunakan IP rooter dan IP Master 
```
echo 'nameserver 192.168.122.1
nameserver 192.233.2.7' > /etc/resolv.conf
```
- Node web server, dan load balancer akan menggunakan IP rooter
```
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
```
Selanjutkan `reload all nodes` dan uji dengan melakukan `ping google.com` pada setiap node

- Majapahit  
![image](https://github.com/user-attachments/assets/3f2692a5-c285-4333-ad05-f0f3dbf56114)
- Mulawarman  
![image](https://github.com/user-attachments/assets/da8382c2-c71d-4133-9834-4aa636884c61)
- GrahamBell  
![image](https://github.com/user-attachments/assets/86d3312f-e152-4aa1-88f4-768b83b8f56f)
- Samaratungga  
![image](https://github.com/user-attachments/assets/abb5fab3-9119-4bc2-a1dd-bf29b26f550b)
- Solok  
![image](https://github.com/user-attachments/assets/94d3f4b5-3bc5-4a23-84c0-a96caed7ed59)
- Srikandi  
![image](https://github.com/user-attachments/assets/d8277975-9a99-4d2e-85bc-3eb93e5c5259)
- Kotalingga  
![image](https://github.com/user-attachments/assets/fd36ec8f-aba4-451c-b87b-147051208afd)
- Bedahulu  
![image](https://github.com/user-attachments/assets/4872cd45-4fc3-4482-a31d-8a58f021de22)
- Tanjungkulai  
![image](https://github.com/user-attachments/assets/57c989bc-bc38-4291-8484-3ddc5f6a59e8)
- Sriwijaya   
![image](https://github.com/user-attachments/assets/a976542c-c8b7-45e7-bf79-e999dbe2fb9a)



## No 2
> Karena para pasukan membutuhkan koordinasi untuk melancarkan serangannya, maka buatlah sebuah domain yang mengarah ke Solok dengan alamat sudarsana.xxxx.com dengan alias www.sudarsana.xxxx.com, dimana xxxx merupakan kode kelompok. Contoh: sudarsana.it01.com.

Jalankan pada node Sriwijaya dan buka file conf  dengan command `nano /etc/bind/named.conf.local`

```
zone "sudarsana.it33.com" {
type master;
file "/etc/bind/jarkom33/sudarsana.it33.com";
};
```

Lalu buat folder jarkom33 sesuai dengan nama pada konfigurasi 

```
mkdir /etc/bind/jarkom33
```

Setelah itu copy file `db.local` menuju folder jarkom33 yang sudah dibuat 

```
cp /etc/bind/db.local /etc/bind/jarkom33/sudarsana.it33.com
```

Lalu buka file dengan `nano /etc/bind/jarkom33/sudarsana.it33.com` lalu edit konfigurasi menjadi seperti berikut dengan IP Solok `192.233.2.2`
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     sudarsana.it33.com. root.sudarsana.it33.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      sudarsana.it33.com.
@       IN      A       192.233.2.2
@       IN      AAAA    ::1
www     IN      CNAME   sudarsana.it33.com.
```
Terakhir restart bind9 dengan command `service bind9 restart`

Setelah itu agar client bisa tersambung dengan domain maka buka konfigurasi tiap client dan tambahkan konfigurasi berikut ini yang merupakan IP dari Sriwijaya (192.233.2.7) sebagai DNS Master, dan IP Majapahit (192.233.1.2) sebagai DNS Slave 
```
up echo nameserver 192.233.2.7 >> /etc/resolv.conf
up echo nameserver 192.233.1.2  >> /etc/resolv.conf
```
Lalu coba cek dengan melakukan command `ping sudarsana.it33.com` pada setiap client untuk mengecek apakah sudah berjalan dengan baik atau belum 

#### Dokumentasi Sudarsana 
- Mulawarman  
![image](https://github.com/user-attachments/assets/281da52c-f758-4303-8313-955abaeb3fb3)
- GrahamBell  
![image](https://github.com/user-attachments/assets/7b61796c-af75-407e-beaf-1ec52c170fc1)
- Samaratungga  
![image](https://github.com/user-attachments/assets/a77be080-e7d4-4e3e-a09a-df14296d56b8)
- Srikandi  
![image](https://github.com/user-attachments/assets/197a6e67-04f8-407d-92e5-328453d02fab)



## No 3
> Para pasukan juga perlu mengetahui mana titik yang akan diserang, sehingga dibutuhkan domain lain yaitu pasopati.xxxx.com dengan alias www.pasopati.xxxx.com yang mengarah ke Kotalingga.

Untuk pengerjaan soal ini sama dengan soal no 2, kita hanya perlu mengubah ip dan domain saja. Berikut kode di dalam file `nano /etc/bind/named.conf.local`

```
zone "pasopati.it33.com" {
type master;
file "/etc/bind/jarkom33/pasopati.it33.com";
};
```
Dan berikut isi konfigurasi yang ada di dalam `nano /etc/bind/jarkom33/pasopati.it33.com`  dengan IP Kotalingga `192.233.2.4`
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     pasopati.it33.com. root.pasopati.it33.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      pasopati.it33.com.
@       IN      A       192.233.2.4
@       IN      AAAA    ::1
www     IN      CNAME   pasopati.it33.com.

```
Terakhir restart bind9 dengan command `service bind9 restart`

Setelah itu agar client bisa tersambung dengan domain maka buka konfigurasi tiap client dan tambahkan konfigurasi berikut ini yang merupakan IP dari Sriwijaya (192.233.2.7) sebagai DNS Master, dan IP Majapahit (192.233.1.2) sebagai DNS Slave 
```
up echo nameserver 192.233.2.7 >> /etc/resolv.conf
up echo nameserver 192.233.1.2  >> /etc/resolv.conf
```
Lalu coba cek dengan melakukan command `ping pasopati.it33.com` pada setiap client untuk mengecek apakah sudah berjalan dengan baik atau belum 
#### Dokumentasi Pasopati
- Mulawarman  
![image](https://github.com/user-attachments/assets/477b664e-8772-4b04-b537-882c0b2e8f15)
- GrahamBell  
![image](https://github.com/user-attachments/assets/3482c324-507d-41a7-8a06-edaa40547d41)
- Samaratungga  
![image](https://github.com/user-attachments/assets/ab84d38f-a3e5-4ea0-b27e-73522c159cb7)
- Srikandi  
![image](https://github.com/user-attachments/assets/2ce27bb2-59be-4b26-a532-4dcb1ea8b3a0)



## No 4
> Markas pusat meminta dibuatnya domain khusus untuk menaruh informasi persenjataan dan suplai yang tersebar. Informasi dan suplai meme terbaru tersebut mengarah ke Tanjungkulai dan domain yang ingin digunakan adalah rujapala.xxxx.com dengan alias www.rujapala.xxxx.com.

Untuk pengerjaan soal ini sama dengan soal no 2, kita hanya perlu mengubah ip dan domain saja. Berikut kode di dalam file `nano /etc/bind/named.conf.local`

```
zone "rujapala.it33.com" {
type master;
file "/etc/bind/jarkom33/rujapala.it33.com";
};
```
Dan berikut isi konfigurasi yang ada di dalam `nano /etc/bind/jarkom33/rujapala.it33.com`  dengan IP Tanjungkulai `192.233.2.6`
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     rujapala.it33.com. root.rujapala.it33.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      rujapala.it33.com.
@       IN      A       192.233.2.6
@       IN      AAAA    ::1
www     IN      CNAME   rujapala.it33.com.

```
Terakhir restart bind9 dengan command `service bind9 restart`

Setelah itu agar client bisa tersambung dengan domain maka buka konfigurasi tiap client dan tambahkan konfigurasi berikut ini yang merupakan IP dari Sriwijaya (192.233.2.7) sebagai DNS Master, dan IP Majapahit (192.233.1.2) sebagai DNS Slave 
```
up echo nameserver 192.233.2.7 >> /etc/resolv.conf
up echo nameserver 192.233.1.2  >> /etc/resolv.conf
```
Lalu coba cek dengan melakukan command `ping rujapala.it33.com` pada setiap client untuk mengecek apakah sudah berjalan dengan baik atau belum 
#### Dokumentasi Rujapala
- Mulawarman  
![image](https://github.com/user-attachments/assets/276bf2f3-910f-40ae-83d1-f036083fa090)
- GrahamBell  
![image](https://github.com/user-attachments/assets/89ef13cf-272b-4d43-a41d-3237deaff334)
- Samaratungga  
![image](https://github.com/user-attachments/assets/0eb71bda-9541-4461-856f-5e067f208392)
- Srikandi  
![image](https://github.com/user-attachments/assets/fa106321-9ac0-45ba-b1f4-dda45d686b54)


## No 5
> Pastikan domain-domain tersebut dapat diakses oleh seluruh komputer (client) yang berada di Nusantara.

Untuk bukti dokumentasi dapat dilihat di bagian atas pada soal 2 - 4, atau klik berikut ini [sudarsana](#dokumentasi-sudarsana), [pasopati](#dokumentasi-pasopati), [rujapala](#dokumentasi-rujapala)
Berikut ini command untuk melakukan ping 
- Sudarsana
```
ping sudarsana.it33.com
ping www.sudarsana.it33.com
```
- Pasopati
```
ping pasopati.it33.com
ping www.pasopati.it33.com
```
- Rujapala
```
ping rujapala.it33.com
ping www.rujapala.it33.com
```
## No 6
> Beberapa daerah memiliki keterbatasan yang menyebabkan hanya dapat mengakses domain secara langsung melalui alamat IP domain tersebut. Karena daerah tersebut tidak diketahui secara spesifik, pastikan semua komputer (client) dapat mengakses domain pasopati.xxxx.com melalui alamat IP Kotalingga (Notes: menggunakan pointer record).

Untuk menyelesaikan soal ini kita bisa menggunakan reverse DNS (Record PTR). Untuk IP Kotalingga yang awalnya adalah `192.233.2.4` akan direverse, sehingga hasilnya adalah `2.233.192`

Jalankan pada Sriwijaya `nano /etc/bind/named.conf.local`

```
zone "2.233.192.in-addr.arpa" {
type master;
file "/etc/bind/jarkom33/2.233.192.in-addr.arpa";
};
```
Setelah itu copy file `db.local` menuju folder jarkom33 yang sudah dibuat 
```
cp /etc/bind/db.local /etc/bind/jarkom33/2.233.192.in-addr.arpa
```
Setelah itu buka file `nano /etc/bind/jarkom33/2.233.192.in-addr.arpa` dan edit konfigurasinya menjadi seperti berikut ini. Perhatikan untuk bagian IP reversenya serta nama domain
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     pasopati.it33.com. root.pasopati.it33.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
2.233.192.in-addr.arpa.         IN      NS      pasopati.it33.com.
4                             	IN      PTR     pasopati.it33.com.

```
Setelah itu restart bind9 dengan `service bind9 restart`

Untuk mengecek apakah sudah berhasil atau belum dapat dilakukan dengan melakukan. Tapi sebelum itu install dnsutils dengan command berikut ini 
```
apt-get update
apt-get install dnsutils
```
Lalu buka node client dan cek dengan command berikut ini 
```
host -t PTR 192.233.2.4
```

#### Dokumentasi 
- Mulawarman  
![image](https://github.com/user-attachments/assets/8ac47470-e10f-4594-a5a9-743d1191d4de)
- GrahamBell  
![image](https://github.com/user-attachments/assets/36571d9e-cb23-4d8e-ab46-728b57e32bb0)
- Samaratungga  
![image](https://github.com/user-attachments/assets/243ca389-7b0d-4c31-bd14-8f8abc2b2bf6)
- Srikandi  
![image](https://github.com/user-attachments/assets/7483c617-eca3-4202-b16d-b28d5db22e36)

## No 7
> Akhir-akhir ini seringkali terjadi serangan brainrot ke DNS Server Utama, sebagai tindakan antisipasi kamu diperintahkan untuk membuat DNS Slave di Majapahit untuk semua domain yang sudah dibuat sebelumnya yang mengarah ke Sriwijaya.

Untuk menyelesaikan soal ini kita harus melakukan konfigurasi pada DNS Master atau Sriwijaya dan DNS Slave atau Majapahit
- Sriwijaya (DNS Master)
Buka file konfigurasi `nano /etc/bind/named.conf.local` dan edit isi file dengan menambahkan konfigurasi berikut dengan IP Majapahit kepada semua zona
```
also-notify { 192.233.1.2; }; // IP Majapahit
allow-transfer { 192.233.1.2; }; // IP Majapahit
```
Sehingga nantinya isi dari file konfigurasi pada Sriwijaya akan berisi seperti berikut ini 
```
zone "sudarsana.it33.com" {
		type master;
		also-notify { 192.233.1.2; }; 
		allow-transfer { 192.233.1.2; }; 
		file "/etc/bind/jarkom33/sudarsana.it33.com";
};

zone "pasopati.it33.com" {
type master;
		also-notify { 192.233.1.2; }; 
		allow-transfer { 192.233.1.2; }; 
file "/etc/bind/jarkom33/pasopati.it33.com";
};

zone "rujapala.it33.com" {
type master;
		also-notify { 192.233.1.2; }; 
		allow-transfer { 192.233.1.2; }; 
file "/etc/bind/jarkom33/rujapala.it33.com";
};

zone "2.233.192.in-addr.arpa" {
type master;
		also-notify { 192.233.1.2; }; 
		allow-transfer { 192.233.1.2; }; 
file "/etc/bind/jarkom33/2.233.192.in-addr.arpa";
};

```
Setelah itu restart bind9 dengan `service bind9 restart`

- Majapahit (DNS Slave)
Pertama install bind9 dengan command berikut ini 
```
apt-get update
apt-get install bind9 -y
```
Lalu nyalakan bind9 dengan `service bind9 start` dan buka file konfigurasi `nano /etc/bind/named.conf.local` dan edit isi konfigurasi seperti berikut ini dengan IP Sriwijaya
```
zone "sudarsana.it33.com" {
		type slave;
		masters { 192.233.2.7; };
		file "/var/lib/bind/sudarsana.it33.com";
};

zone "pasopati.it33.com" {
		type slave;
		masters { 192.233.2.7; }; 
		file "/var/lib/bind/pasopati.it33.com";
};

zone "rujapala.it33.com" {
		type slave;
		masters { 192.233.2.7; }; 
		file "/var/lib/bind/rujapala.it33.com";
};

zone "2.233.192.in-addr.arpa" {
		type slave;
		masters { 192.233.2.7; }; 
		file "/var/lib/bind/2.233.192.in-addr.arpa";
};

```
Setelah itu restart bind9 dengan `service bind9 restart`  

Untuk mengecek apakah sudah berhasil atau belum bisa dilakukan dengan mengirimkan command `service bind9 stop` pada Sriwijaya, dan mencoba melakukan ping kepada client 

#### Dokumentasi
- Mulawarman  
![image](https://github.com/user-attachments/assets/9833d103-78ed-4c52-820c-61ced8a6cffa)
- GrahamBell  
![image](https://github.com/user-attachments/assets/1a03ad39-0dd4-40de-ba06-29dc5e10dd1e)
- Samaratungga  
![image](https://github.com/user-attachments/assets/3f7ce51f-997c-4e4d-82a4-cbd84f896853)
- Srikandi  
![image](https://github.com/user-attachments/assets/2ef283a4-8956-4bd1-95e7-fa9bd3d5c7e9)


## No 8
> Kamu juga diperintahkan untuk membuat subdomain khusus melacak kekuatan tersembunyi di Ohio dengan subdomain cakra.sudarsana.xxxx.com yang mengarah ke Bedahulu.
Untuk menyelesaikan no 8 kita harus mengedit isi konfigurasi pada Sriwijaya dengan domain sudarsana dengan mengirimkan command `nano /etc/bind/jarkom33/sudarsana.it33.com` lalu tambahkan konfigurasi berikut dengan IP milik Bedahulu `192.233.2.5`
```
cakra		IN      A       10.73.1.5
www.cakra	IN      CNAME   cakra.sudarsana.it33.com.

```
Sehingga isi dari file konfigurasi sudarsana secara keseluruhan akan menjadi seperti berikut ini 
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     sudarsana.it33.com. root.sudarsana.it33.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      sudarsana.it33.com.
@       IN      A       192.233.2.2
@       IN      AAAA    ::1
www     IN      CNAME   sudarsana.it33.com.
cakra		IN      A       10.73.1.5
www.cakra	IN      CNAME   cakra.sudarsana.it33.com.
```
Setelah itu restart bind9 dengan `service bind9 restart` dan lakukan cek tes ping kepada node client dengan command berikut ini
```
ping cakra.sudarsana.it.33.com
```

#### Dokumentasi
- Mulawarman  
![image](https://github.com/user-attachments/assets/1b595b22-4252-4ed3-ba7c-b78b3213be53)
- GrahamBell  
![image](https://github.com/user-attachments/assets/24c899e1-8eae-45c3-8524-b494734c7bd9)
- Samaratungga  
![image](https://github.com/user-attachments/assets/0327ee7d-c846-4a82-a3c1-45fa52f46e83)
- Srikandi  
![image](https://github.com/user-attachments/assets/e199c0d2-82fe-4f5a-bbd7-e7e3c9528dd5)



## No 9
> Karena terjadi serangan DDOS oleh shikanoko nokonoko koshitantan (NUN), sehingga sistem komunikasinya terhalang. Untuk melindungi warga, kita diperlukan untuk membuat sistem peringatan dari siren man oleh Frekuensi Freak dan memasukkannya ke subdomain panah.pasopati.xxxx.com dalam folder panah dan pastikan dapat diakses secara mudah dengan menambahkan alias www.panah.pasopati.xxxx.com dan mendelegasikan subdomain tersebut ke Majapahit dengan alamat IP menuju radar di Kotalingga.

## No 10
> Markas juga meminta catatan kapan saja meme brain rot akan dijatuhkan, maka buatlah subdomain baru di subdomain panah yaitu log.panah.pasopati.xxxx.com serta aliasnya www.log.panah.pasopati.xxxx.com yang juga mengarah ke Kotalingga.

## No 11
> Setelah pertempuran mereda, warga IT dapat kembali mengakses jaringan luar dan menikmati meme brainrot terbaru, tetapi hanya warga Majapahit saja yang dapat mengakses jaringan luar secara langsung. Buatlah konfigurasi agar warga IT yang berada diluar Majapahit dapat mengakses jaringan luar melalui DNS Server Majapahit.

## No 12
> Karena pusat ingin sebuah laman web yang ingin digunakan untuk memantau kondisi kota lainnya maka deploy laman web ini (cek resource yg lb) pada Kotalingga menggunakan apache.

## No 13
> Karena pusat ingin sebuah laman web yang ingin digunakan untuk memantau kondisi kota lainnya maka deploy laman web ini (cek resource yg lb) pada Kotalingga menggunakan apache.

## No 14
> Selama melakukan penjarahan mereka melihat bagaimana web server luar negeri, hal ini membuat mereka iri, dengki, sirik dan ingin flexing sehingga meminta agar web server dan load balancer nya diubah menjadi nginx.

## No 15
> Markas pusat meminta laporan hasil benchmark dengan menggunakan apache benchmark dari load balancer dengan 2 web server yang berbeda tersebut dan meminta secara detail dengan ketentuan:  
Nama Algoritma Load Balancer  
Report hasil testing apache benchmark   
Grafik request per second untuk masing masing algoritma.   
Analisis  
Meme terbaik kalian (terserah ( ͡° ͜ʖ ͡°)) 🤓  

## No 16
> Karena dirasa kurang aman dari brainrot karena masih memakai IP, markas ingin akses ke Solok memakai solok.xxxx.com dengan alias www.solok.xxxx.com (sesuai web server terbaik hasil analisis kalian).

## No 17
> Agar aman, buatlah konfigurasi agar solok.xxx.com hanya dapat diakses melalui port sebesar π x 10^4 = (phi nya desimal) dan 2000 + 2000 log 10 (10) +700 - π = ?.

## No 18
> Apa bila ada yang mencoba mengakses IP solok akan secara otomatis dialihkan ke www.solok.xxxx.com.

## no. 19
> Karena probset sudah kehabisan ide masuk ke salah satu worker buatkan akses direktori listing yang mengarah ke resource worker2.

## No. 20
> Worker tersebut harus dapat di akses dengan sekiantterimakasih.xxxx.com dengan alias www.sekiantterimakasih.xxxx.com.
