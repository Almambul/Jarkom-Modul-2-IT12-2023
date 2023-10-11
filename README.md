# Jarkom-Modul-2-IT12-2023
Anggota Kelompok : 
1. Raditya Pratama - 5027211047
2. Salmaa Satifha Dewi - 5027211011

# Soal 1
## Screenshot
![image](https://github.com/Almambul/Jarkom-Modul-2-IT12-2023/assets/107543354/7591c410-26c9-46cf-84e5-901f88a0360c)
## Cara Pengerjaan
1. Membuat topologi yang diminta pada GNS web setelah melakukan start pada virtual box
2. Menghubungkan garis antara node 1 dengan node lainnya
3. Melakukan konfigurasi prefix IP
```
auto eth0
iface eth0 inet static
	address 192.239.1.2
	netmask 255.255.255.0
	gateway 192.239.1.1

auto eth0
iface eth0 inet static
	address 192.239.1.3
	netmask 255.255.255.0
	gateway 192.239.1.1

auto eth0
iface eth0 inet static
	address 192.239.2.2
	netmask 255.255.255.0
	gateway 192.239.2.1

auto eth0
iface eth0 inet static
	address 192.239.2.3
	netmask 255.255.255.0
	gateway 192.239.2.1

auto eth0
iface eth0 inet static
	address 192.239.3.2
	netmask 255.255.255.0
	gateway 192.239.3.1

auto eth0
iface eth0 inet static
	address 192.239.3.3
	netmask 255.255.255.0
	gateway 192.239.3.1

auto eth0
iface eth0 inet static
	address 192.239.3.4
	netmask 255.255.255.0
	gateway 192.239.3.1

auto eth0
iface eth0 inet static
	address 192.239.3.5
	netmask 255.255.255.0
	gateway 192.239.3.1
```
4. Menjalankan command ```nano ~/.bashrc```
5. Menjalankan command 
```iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.239.0.0/16```
6. Menjalankan command untuk mencari IP DNS dengan 
```cat /etc/resolv.conf```
7. Menjalankan command ```source ~/.bashrc```
8. Pada setiap masing-masing node melakukan 2 command untuk memastikan dapat melakukan ping yaitu berupa
```echo nameserver 192.168.122.1 > /etc/resolv.conf```
```ping google.com```

## Kendala yang Dihadapi
Tidak mengalami kendala

# Soal 2
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi
1. server arjuna tidak bisa ditemukan

# Soal 3
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi
1. server abimanyu tidak bisa ditemukan
