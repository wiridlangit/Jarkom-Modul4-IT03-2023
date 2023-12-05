![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/cce7b98e-0c47-4ae7-bde0-f631b42be1a2)# Jarkom-Modul4-IT03-2023

# Kelompok: IT03
### Anggota: 
Nama | NRP | Github 
--- | --- | --- |
Adiba Zalfa Camilla | 5027211060 | https://github.com/dibazalfa
Wiridlangit Suluh Jiwangga | 5027211064 | https://github.com/wiridlangit

# IP Prefix
`10.65`

# Spreadsheet
https://docs.google.com/spreadsheets/d/19JmbFhPwqb_NZPzJGkuDSPquwvK9HBtlMVNgrxmwAjY/edit?pli=1#gid=1936683207

## Daftar Isi 
- [Topologi](#topologi)
- [Rute Subnet](#rute-subnet)
- [VLSM](#vlsm)
- [CIDR](#cidr)

# Topologi
### Cisco Packet Tracer | VLSM |
![Topologi_Modul4_Subnet_Final](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/41efa918-f229-4eae-b723-450ff6e48a83)

### GNS3 | CIDR |
![WhatsApp Image 2023-12-02 at 02 34 45_9b027623](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/00166b77-e52e-416c-934f-a9977de13a3f)

# Rute Subnet
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/7106a1af-5024-49ee-8cee-fc3686ccfc4c)

# VLSM
VLSM digunakan pada Cisco Packet Tracer (CPT)

## Tree VLSM
Berikut adalah Tree yang digunakan sebagai visualisasi VLSM.
<img width="6491" alt="VLSM Tree" src="https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/0fb14b81-bbf1-44ae-8045-617f6b5ad8ec">

## Pembagian IP VLSM
Berikut adalah pembagian IP pada VLSM.
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/35ae9568-74e5-412f-8868-eb31bed35754)

## Konfigurasi CPT
Konfigurasi IP pada CPT bisa dilakukan dengan cara sebagai berikut:

1. Setelah menentukan semua subnet, pertama buka node router aura lalu masukan IP berdasarkan arah eth pada subnet yang dituju:
![Screenshot 2023-12-05 190136](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/d741aad8-dc37-43a8-8951-83978e7b6719)
Arah yang dituju sebagai contoh pertama yaitu mengarah ke subnet A1 dengan melalui eth1/0

2. Pilih pada bagian eth1/0 lalu dalam IP Configuration masukan IP `10.65.24.113`. IP `10.65.24.113` didapatkan dengan melihat data pembagian IP subnet A1 pada sheets `10.65.24.112` lalu ditambahkan 1 digit pada angka belakangnya. Untuk netmask disamakan seperti pada sheets.
![Screenshot 2023-12-05 190153](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/b7a3a9fc-d577-4677-8ec4-c717162c088b)

3. Lalu pilih node router lainnya pada A1, yaitu Frieren. Pilih arah eth yang menuju ke A1 dalam hal ini eth1/0 lalu lakukan konfigurasi dengan cara yang sama yaitu menambahkan 1 digit lagi pada IP sebelumnya  `10.65.24.114`.
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/a1d933ed-9c34-454e-ae48-d814c6409efe)
Lakukan hal yang sama untuk setiap node dan arah eth pada topologi.

## Routing CPT
Konfigurasi routing untuk menghubungkan antara subnet.

1. Sebagai langkah awal buka node router lalu pilih pada section Routing > Static.
2. Lalu pada bagian Network dan Mask masukan sesuai data subnet yang dituju dan diisi dengan data yang sama pada sheets.
3. Next Hop diisi dengan node router terdekat yang berperan menjadi "jembatan".

Sebagai contoh, node router Aura ingin menuju client Lakekorridor. Aura harus melalui subnet A1 dan singgah di frieren lalu melanjutkan perjalanan melalui subnet A2 hingga sampai ke Lakekorridor.

1. Pada node router Aura masukan kolom Network dan Mask subnet A2 yaitu `10.65.24.64` dan `255.255.255.224`. Pada kolom Next Hop masukan IP eth1/0 pada node router Frieren yaitu `10.65.24.114`.
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/da3e40ab-404e-4c34-b375-a018dabf5b21)

2. Pada node router Frieren masukan kolom Network dan Masuk dengan IP `0.0.0.0` dan Next Hop yaitu `10.65.24.113` sesuai dengan eth1/0 subnet A1 pada node router Aura.
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/113527799/f847f6bc-2da5-47ee-a0de-45889eae5c81)
Dengan ini subnet A1 dan A2 sudah terhubung.

3. Lakukan hal ini pada setiap router yang mewakili client dan ingin dihubungkan.

*Notes: Memilih IP `0.0.0.0` dilakukan ketika Router mengarah kembali ke Router utama yaitu Aura. Sebagai contoh dari node router Flamme ke Frieren pada Network dan Mask menggunakan IP `0.0.0.0` karena mengarah kembali ke node router utama yaitu Aura.

# CIDR
CIDR digunakan pada GNS3

## Penggabungan Subnet 

### Step I
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/b046a157-321b-464b-91a1-b724bf913031)

### Step II
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/ad7c88dd-1a56-440d-83c6-42791f527143)

### Step III
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/6ac87696-1567-4884-a11a-c34d5dc47ec1)

### Step IV
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/7ca431b5-bf93-4892-9420-d5a5b6b4fc92)

### Step V
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/aa94cd79-0969-44ba-94ed-0681efb268fd)

### Step VI
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/a62b5937-4e9b-4f9b-b426-22a51ebd4f44)

### Step VII
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/77a42efd-4711-476f-aaa5-cf07d4350fce)

### Step VIII
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/a58fa636-0191-4bb7-a21c-3e25dd1203d7)

### Step IX
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/e851d8a8-dc59-4498-bb3a-c4700e3061c1)

Didapatkan netmask akhir pada I1 adalah `/14`

## Pembagian IP CIDR
![image](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/beb580b1-07a5-4861-a84b-319ee45aca21)

## Tree CIDR 
![IT03_CIDR Tree](https://github.com/wiridlangit/Jarkom-Modul4-IT03-2023/assets/103043684/e20b3b63-d8bd-49ad-9410-7af41951ef5e)

## Routing
Lakukan konfigurasi berikut, 
#### Aura
```
auto eth0
iface eth0 inet dhcp

#A20 Aura-Denken
auto eth1
iface eth1 inet static
	address 10.67.1.1
	netmask 255.255.255.252

#A9 Aura-Eisen
auto eth2
iface eth2 inet static
	address 10.65.128.1
	netmask 255.255.255.252

#A1 Aura-Frieren
auto eth3
iface eth3 inet static
	address 10.66.128.1
	netmask 255.255.255.252
```
#### Denken
```
#A20 Denken-Aura
auto eth0
iface eth0 inet static
	address 10.67.1.2
	netmask 255.255.255.252

#A21 Denken-Switch-RoyalCapital-Switch-WileRegion
auto eth1
iface eth1 inet static
	address 10.67.0.1
	netmask 255.255.255.0
```
#### RoyalCapital
```
auto eth0
iface eth0 inet static
	address 10.67.0.2
	netmask 255.255.255.0
	gateway 10.67.0.1
```
#### WilleRegion
```
auto eth0
iface eth0 inet static
	address 10.67.0.3
	netmask 255.255.255.0
	gateway 10.67.0.1
```
#### Eisen
```
#A9 Aura-Eisen
auto eth0
iface eth0 inet static
	address 10.65.128.2
	netmask 255.255.255.252

#A11 Eisen-Switch-Stark
auto eth1
iface eth1 inet static
	address 10.65.16.1
	netmask 255.255.255.252

#A12 Eisen-Lugner
auto eth2
iface eth2 inet static
	address 10.65.8.1
	netmask 255.255.255.252

#A15 Eisen-Linie
auto eth3
iface eth3 inet static
	address 10.65.96.1
	netmask 255.255.255.252

#A10 Eisen-Switch-Richter-Switch-Revolte
auto eth4
iface eth4 inet static
	address 10.65.32.1
	netmask 255.255.255.248
```
#### Stark
```
#A11 Stark-Switch-Eisen
auto eth0
iface eth0 inet static
	address 10.65.16.2
	netmask 255.255.255.252
	gateway 10.65.16.1
```
Kemudian, lakukan routing 
#### Aura
route add -net 10.67.0.0 netmask 255.255.255.0 gw 10.67.1.2
route add -net 10.65.16.0 netmask 255.255.255.252 gw 10.65.128.2 

#### Denken
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.67.1.1

#### Eisen
route add -net 0.0.0.0 netmask 0.0.0.0 gw 10.65.128.1
