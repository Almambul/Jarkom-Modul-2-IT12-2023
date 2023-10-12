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
```
#!/bin/bash

config() {
    if ! dpkg -l | grep -q bind9; then
	su -c "apt-get install sudo"
        sudo apt-get update
        sudo apt-get install -y sudo bind9 nano
    fi

    # Create a zone configuration for "www.arjuna.it12.com"
    sudo bash -c 'cat <<EOL > /etc/bind/named.conf.local
zone "arjuna.it12.com" {
    type master;
    notify yes;
    also-notify { 192.239.2.3; };
    allow-transfer { 192.239.2.3; };
    file "/etc/bind/jarkom/arjuna.it12.com";
};

zone "abimanyu.it12.com" {
    type master;
    notify yes;
    also-notify { 192.239.2.3; };
    allow-transfer { 192.239.2.3; };
    file "/etc/bind/jarkom/abimanyu.it12.com";
};

zone "2.239.192.in-addr.arpa" {
    type master;
    file "/etc/bind/jarkom/2.239.192.in-addr.arpa";
};
EOL'

    # Generate the DNS records in the zone file with updated TTL and CNAME
    sudo bash -c 'cat <<EOL > /etc/bind/jarkom/arjuna.it12.com
\$TTL 604800
@ IN SOA arjuna.it12.com. root.arjuna.it12.com. (
    2	; Serial
    604800	; Refresh
    86400	; Retry
    2419200	; Expire
    604800 ); Negative Cache TTL
@ IN NS arjuna.it12.com.
@ IN A 192.239.3.2   ; IP address of your server
@ IN AAAA ::1
www in CNAME arjuna.it12.com.
EOL'

    # Generate the DNS records in the zone file with updated TTL and CNAME
    sudo bash -c 'cat <<EOL > /etc/bind/jarkom/abimanyu.it12.com
\$TTL 604800
@ IN SOA abimanyu.it12.com. root.abimanyu.it12.com. (
    2	; Serial
    604800	; Refresh
    86400	; Retry
    2419200	; Expire
    604800 ); Negative Cache TTL
@ IN NS abimanyu.it12.com.
@ IN A 192.239.3.4   ; IP address of your server
@ IN AAAA ::1
www in CNAME abimanyu.it12.com.
www.parikesit IN CNAME abimanyu.it12.com.
EOL'

    # Generate the DNS records in the zone file with updated TTL and CNAME
    sudo bash -c 'cat <<EOL > /etc/bind/jarkom/2.239.192.in-addr.arpa
\$TTL 604800
@ IN SOA abimanyu.it12.com. root.abimanyu.it12.com. (
    2	; Serial
    604800	; Refresh
    86400	; Retry
    2419200	; Expire
    604800 ); Negative Cache TTL
2.239.192.in-addr.arpa IN NS abimanyu.it12.com.
2 IN PTR abimanyu.com.
EOL'

    # Restart BIND to apply the new configuration using 'systemctl'
    service bind9 restart

    echo "DNS Master (www.arjuna.it12.com) configured."
}

# Run the configure function
config
```
## Kendala yang Dihadapi
1. server arjuna tidak bisa ditemukan

# Soal 3
## Screenshot
## Cara Pengerjaan
## Kendala yang Dihadapi
1. server abimanyu tidak bisa ditemukan
