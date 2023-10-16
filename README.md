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
![WhatsApp Image 2023-10-16 at 17 19 07](https://github.com/Almambul/Jarkom-Modul-2-IT12-2023/assets/107543354/9c033405-7abc-405d-8b40-da568b0fb3c2)
## Cara Pengerjaan
1. Melakukan update ```apt-get update```
2. Menginstall bind9
```apt-get install bind9 -y```   
3. Membuka text editor /etc/bind/named/conf.local
```nano /etc/bind/named.conf.local```
4. Mengisi konfigurasi domain arjuna.IT12.com
```
zone "arjuna.IT12.com" {
        type master;
        file "/etc/bind/jarkom/arjuna.IT12.com";
};
```
5. Membuat folder /etc/bind/jarkom
```
mkdir /etc/bind/jarkom
```
6. Menyalin file db.local pada path /etc/bind/db.local ke dalam folder jarkom arjuna.IT12.com
```
cp /etc/bind/db.local /etc/bind/jarkom/arjuna.IT12.com
```
7. Membuka text editor /etc/bind/jarkom/arjuna.IT12.com
```
nano /etc/bind/jarkom/arjuna.IT12.com
```
8. Mengedit IP menyesuaikan kode kelompok
```
;
;BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     arjuna.IT12.com. root.arjuna.IT12.com. (
                2               ; Serial
                604800          ; Refresh
                86400           ; Retry
                2419200         ; Expire
                604800 )        ; Negative Cache TTL
;
@       IN      NS      arjuna.IT12.com.
@       IN      A       192.241.3.5
www     IN      CNAME 	arjuna.IT12.com.
```
9. Restart bind9
```
service bind9 restart
```
10. Membuka text editor /etc/resolv.conf
```
nano /etc/resolv.conf
```
11. Mencantumkan alamat IP
```
nameserver 192.168.122.1
```
12. Mengupdate dan menginstall dnsutils
```
apt-get update 
apt-get install dnsutils -y
```
13.  Membuka text editor /etc/resolv.conf
```
nano /etc/resolv.conf
```
14. Mengubah alamat IP
```
nameserver 192.239.2.2
```
15. Melakukan nslookup
```
nslookup arjuna.IT12.com
```

## Kendala yang Dihadapi
1. server arjuna tidak bisa ditemukan

# Soal 3
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi
1. server abimanyu tidak bisa ditemukan

# Soal 4
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi


# Soal 5
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi


# Soal 6
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi

# Soal 7
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi


# Soal 8
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi


# Soal 9
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi


# Soal 10
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi


# Soal 11
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi


# Soal 12
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi


# Soal 13
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi

# Soal 14
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi

# Soal 15
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi

# Soal 16
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi

# Soal 17
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi

# Soal 18
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi

# Soal 19
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi

# Soal 20
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi
