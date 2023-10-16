# Jarkom-Modul-2-IT12-2023
Anggota Kelompok : 
1. Raditya Pratama - 5027211047
2. Salmaa Satifha Dewi - 5027211011

# Soal 1
## Screenshot
![image](https://github.com/Almambul/Jarkom-Modul-2-IT12-2023/assets/107543354/7591c410-26c9-46cf-84e5-901f88a0360c)
![WhatsApp Image 2023-10-16 at 17 19 07](https://github.com/Almambul/Jarkom-Modul-2-IT12-2023/assets/107543354/9c033405-7abc-405d-8b40-da568b0fb3c2)
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
![no2fix](https://github.com/Almambul/Jarkom-Modul-2-IT12-2023/assets/107543354/2f5aebbb-ebd6-44b0-b936-dccacb1162f9)
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
![no2](https://github.com/Almambul/Jarkom-Modul-2-IT12-2023/assets/107543354/95c1bb9c-95bc-4279-af6b-bfc2cd04dfd5)
## Cara Pengerjaan
1. Membuka text editor /etc/bind/named/conf.local
```nano /etc/bind/named.conf.local```
2. Mengisi konfigurasi domain abimanyu.IT12.com
```
zone "abimanyu.IT12.com" {
        type master;
        file "/etc/bind/jarkom/abimanyu.IT12.com";
};
```
3. Menyalin file db.local pada path /etc/bind/db.local ke dalam folder jarkom abimanyu.IT12.com
```
cp /etc/bind/db.local /etc/bind/jarkom/abimanyu.IT12.com
```
4. Membuka text editor /etc/bind/jarkom/abimanyu.IT12.com
```
nano /etc/bind/jarkom/abimanyu.IT12.com
```
5. Mengedit IP menyesuaikan kode kelompok
```
;
;BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     abimanyu.IT12.com. root.abimanyu.IT12.com. (
                2               ; Serial
                604800          ; Refresh
                86400           ; Retry
                2419200         ; Expire
                604800 )        ; Negative Cache TTL
;
@       IN      NS      abimanyu.IT12.com.
@       IN      A       192.241.3.3
www     IN      CNAME 	abimanyu.IT12.com.
```
6. Restart bind9
```
service bind9 restart
```
7. Membuka text editor /etc/resolv.conf
```
nano /etc/resolv.conf
```
8. Mencantumkan alamat IP
```
nameserver 192.168.122.1
```
9. Mengupdate dan menginstall dnsutils
```
apt-get update 
apt-get install dnsutils -y
```
10.  Membuka text editor /etc/resolv.conf
```
nano /etc/resolv.conf
```
11. Mengubah alamat IP
```
nameserver 192.239.2.2
```
12. Melakukan nslookup
```
nslookup abimanyu.IT12.com
```

## Kendala yang Dihadapi
1. server abimanyu tidak bisa ditemukan


# Soal 4
## Screenshot
![no4](https://github.com/Almambul/Jarkom-Modul-2-IT12-2023/assets/107543354/6b251309-d705-4bfa-9c1b-eab09e72b46a)
## Cara Pengerjaan
1. Membuka text editor /etc/bind/jarkom/abimanyu.IT12.com
```
nano /etc/bind/jarkom/abimanyu.IT12.com
```
2. Mengedit dan menambahkan konfigurasi menjadi
```
;
;BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     abimanyu.IT12.com. root.abimanyu.IT12.com. (
                2               ; Serial
                604800          ; Refresh
                86400           ; Retry
                2419200         ; Expire
                604800 )        ; Negative Cache TTL
;
@       IN      NS      abimanyu.IT12.com.
@       IN      A       192.239.3.3
www     IN      CNAME   abimanyu.IT12.com.
parikesit IN	A	192.239.3.3
```
3. Melakukan service bind
```
service bind9 restart
```
4. Mencoba ping ke subdomain
```
ping parikesit.abimanyu.IT12.com
```
## Kendala yang Dihadapi
Tidak ada kendala yang ditemukan


# Soal 5
## Screenshot
![no5](https://github.com/Almambul/Jarkom-Modul-2-IT12-2023/assets/107543354/855f230c-259e-4fb1-b123-19120a9d71ac)
## Cara Pengerjaan
1. Membuka text editor /etc/bind/named.conf.local
```
nano /etc/bind/named.conf.local
```
2. Menambahkan konfigurasi reverse dari 3 byte awal dari IP abimanyu ke dalam file named.conf.local
```
zone "3.239.192.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/3.239.192.in-addr.arpa";
};
```
3. Menyalin file db.lokal pada path /etc/bind ke folder jarkom, lalu mengubah nama menjadi 3.239.192.in-addr.arpa
```
cp /etc/bind/db.local /etc/bind/jarkom/3.239.192.in-addr.arpa
```
4. Membuka text editor /etc/bind/jarkom/3.239.192.in-addr.arpa
```
nano /etc/bind/jarkom/3.239.192.in-addr.arpa
```
5. Restart bind9
```
service bind9 restart
```
6. Melakukan update dan install dnsutils
```
apt-get update
apt-get install dnsutils
```
7. Mengecek konfigurasi sudah benar atau belum pada node nakula
```host -t PTR 192.239.3.3```

## Kendala yang Dihadapi
Tidak ada kendala yang ditemukan


# Soal 6
## Screenshot
![WhatsApp Image 2023-10-16 at 18 13 43](https://github.com/Almambul/Jarkom-Modul-2-IT12-2023/assets/107543354/0f2ae580-b857-48d8-9cfe-0e63048b34c2)
## Cara Pengerjaan
1. Membuka text editor /etc/bind/named.conf.local
2. Menyesuaikan zone abimanyu menjadi
```
zone "abimanyu.IT12.com" {
    type master;
    notify yes;
    also-notify { 192.239.2.3; };
    allow-transfer { 192.239.2.3; };
    file "/etc/bind/jarkom/abimanyu.IT12.com";
};
```
3. Melakukan restart bind9
```
service bind9 restart
```
4. Membuka node werkudara, melakukan update dan menginstall bind9
```
apt-get update
apt-get install bind9 -y
```
5. Membuka text editor /etc/bind/named.conf.local
```
nano /etc/bind/named.conf.local
```
6. Menyesuaikan zone menjadi
```
zone "abimanyu.IT12.com" {
    type slave;
    masters { 192.239.2.2; };
    file "/var/lib/bind/abimanyu.IT12.com";
};

```
7. Melakukan restart bind9
```
service bind9 restart
```
8. Membuka node yudhistira dan menghentikan bind9 dari yudhistira
```
service bind9 stop
```
9. Membuka node nakula sebagai client
```
nano /etc/resolv.conf
```
10. Menambahkan nameserver dari werkudara menjadi
```
echo nameserver 192.239.2.2
echo nameserver 192.239.2.3
``` 
11. Melakukan pengecekan ping ke abimanyu.IT12.com pada node nakula sebagai client
```
ping abimanyu.IT12.com
```
## Kendala yang Dihadapi
Tidak ada kendala yang ditemukan


# Soal 7
## Screenshot
## Cara Pengerjaan
1. Membuka text editor /etc/bind/jarkom/abimanyu.IT12.com
```nano /etc/bind/jarkom/abimanyu.IT12.com```
2. Melakukan modifikasi menjadi
```
;
;BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     abimanyu.IT12.com. root.abimanyu.IT12.com. (
                2               ; Serial
                604800          ; Refresh
                86400           ; Retry
                2419200         ; Expire
                604800 )        ; Negative Cache TTL
;
@       IN      NS      abimanyu.IT12.com.
@       IN      A       192.239.3.3
www     IN      CNAME   abimanyu.IT12.com.
parikesit IN 	A 	192.239.3.3
ns1 	IN 	A	192.239.3.3
baratayuda IN 	NS 	ns1
```
3. Membuka text editor /etc/bind/named.conf.options
```nano /etc/bind/named.conf.options```
4. Menambahkan ```allow-query{any;};``` pada isi file
5. Beralih ke node werkudara, membuka text editor /etc/bind/named.conf.options
```/etc/bind/named.conf.options```
6. Menambahkan ```allow-query{any;};``` pada isi file
7. Membuat folder baratayuda
```mkdir /etc/bind/baratayuda```
8. Memindahkan db.local ke baratayuda.abimanyu.IT12.com
```cp /etc/bind/db.local /etc/bind/delegasi/its.jarkom2022.com```
9. Restart bind9
```service bind9 restart```
10. Melakukan pengecekan
```ping baratayuda.abimanyu.IT12.com```
## Kendala yang Dihadapi
1. Error ketika melakukan testing

# Soal 8
## Screenshot
## Cara Pengerjaan
1. Membuka text editor /etc/bind/named.conf.local
```nano /etc/bind/named.conf.local```
2. Menambahkan konfigurasi berupa
```
zone "rjp.baratayuda.abimanyu.it12.com" {
    type master;
    file "/etc/bind/zones/rjp.baratayuda.abimanyu.it12.com.";
};
```
3. Membuat text editor /etc/bind/zones/rjp.baratayuda.abimanyu.it12.com
```
nano /etc/bind/zones/rjp.baratayuda.abimanyu.it12.com
```
4. Melakukan modifikasi isi file menjadi
```
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     rjp.baratayuda.abimanyu.it12.com. root.rjp.baratayuda.abimanyu.it11.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      rjp.baratayuda.abimanyu.it12.com.

; DNS Records
@           IN      A       192.239.3.3
www         IN      CNAME   rjp.baratayuda.abimanyu.it12.com.
```
5. Melakukan restart bind9
```
service bind9 restart
```
6. Melakukan pengecekan
```
ping rjp.baratayuda.abimanyu.IT12.com
```
## Kendala yang Dihadapi
Tidak ada kendala yang ditemukan

# Soal 9
## Screenshot
## Cara Pengerjaan
1. Membuat text editor /var/www/jarkom/index.php pada node prabukusuma
```nano /var/www/jarkom/index.php```
2. Memasukkan kode php Halo
```
<?php
echo "Hello World from prabukusuma";
?>
```
3. Membuat text editor /etc/nginx/sites-available/jarkom
```nano /etc/nginx/sites-available/jarkom```
4. Memodifikasi isi file konfigurasi
```
server {
    listen 8001;
    root /var/www/jarkom;
    index index.php index.html index.htm;
    server_name _;
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }
    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
    }
    location ~ /\.ht {
        deny all;
    }
    error_log /var/log/nginx/jarkom_error.log;
    access_log /var/log/nginx/jarkom_access.log;
}
```
5. Menjalankan command ```ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled/jarkom```
6. Menghapus /etc/nginx/sites-enabled/default
```rm /etc/nginx/sites-enabled/default```
7. Melakukan restart nginx
```service nginx restart```
8. Menjalankan command
```
service php7.2-fpm start
service php7.2-fpm status
```
9. Mengakses menggunakan ```lynx http://10.69.3.2:8001```
10. Membuat text editor /var/www/jarkom/index.php pada node wisanggeni
```nano /var/www/jarkom/index.php```
11. Menambahkan isi file dengan
```
<?php
echo "Hello World";
?>
```
12. Membuat text editor /etc/nginx/sites-available/jarkom
```nano /etc/nginx/sites-available/jarkom```
13. Melakukan modifikasi berupa
```
server {
    listen 8003;
    root /var/www/jarkom;
    index index.php index.html index.htm;
    server_name _;
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }
    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
    }
    location ~ /\.ht {
        deny all;
    }
    error_log /var/log/nginx/jarkom_error.log;
    access_log /var/log/nginx/jarkom_access.log;
}
```
14. Menjalankan command seperti pada node prabukusuma berupa
```
ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled/jarkom
rm /etc/nginx/sites-enabled/default
service nginx restart
service php7.2-fpm start
service php7.2-fpm status
```
15. Mengakses menggunakan ```lynx http://10.69.3.3:8003```
16. Membuat text editor /var/www/jarkom/index.php pada node wisanggeni
```nano /var/www/jarkom/index.php```
17. Menambahkan isi file dengan
```
<?php
echo "Hello World";
?>
```
18. Membuat text editor /etc/nginx/sites-available/jarkom pada node abimanyu
```nano /etc/nginx/sites-available/jarkom```
19. Melakukan modifikasi berupa
```
server {
    listen 8002;
    root /var/www/jarkom;
    index index.php index.html index.htm;
    server_name _;
    location / {
        try_files $uri $uri/ /index.php?$query_string;
    }
    location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.2-fpm.sock;
    }
    location ~ /\.ht {
        deny all;
    }
    error_log /var/log/nginx/jarkom_error.log;
    access_log /var/log/nginx/jarkom_access.log;
}
```
20. Menjalankan command seperti pada node prabukusuma dan wisanggeni berupa
```
ln -s /etc/nginx/sites-available/jarkom /etc/nginx/sites-enabled/jarkom
rm /etc/nginx/sites-enabled/default
service nginx restart
service php7.2-fpm start
service php7.2-fpm status
```
21. Mengakses menggunakan ```lynx http://10.69.3.3:8002```
## Kendala yang Dihadapi
Tidak ada kendala yang ditemukan

# Soal 10
## Screenshot
## Cara Pengerjaan
1. Membuat text editor /etc/nginx/sites-available/load-balancer pada node arjuna sebagai load balancer
```nano /etc/nginx/sites-available/load-balancer```
2. Memodifikasi konfigurasi berupa
```
upstream webserver {
    server 10.69.3.2:8001; # Prabukusuma
    server 10.69.3.3:8002; # Abimanyu
    server 10.69.3.4:8003; # Wisanggeni
}
server {
    listen 80;
    server_name arjuna.it11.com www.arjuna.it12.com;
    location / {
        proxy_pass http://webserver;
    }
}
```
3. Menjalankan command
```
ln -s /etc/nginx/sites-available/load-balancer /etc/nginx/sites-enabled/load-balancer
```
4. Restart nginx
```
service nginx restart
```
6. Mengakses menggunakan
```
lynx http://www.arjuna.it12.com
```
## Kendala yang Dihadapi
Tidak ada kendala yang ditemukan

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
