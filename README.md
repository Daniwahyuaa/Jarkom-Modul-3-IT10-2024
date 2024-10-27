# Jarkom-Modul-3-IT10-2024
Kelompok IT 10
| No | Nama                 | NRP         |
|----|----------------------|---------------------------|
| 1  | dani Wahyu            | 5027231038                    |
| 2  | Abid Ubaidillah       | 5027231089                  | 
---
## Topology
![image](https://github.com/user-attachments/assets/459b0221-7aa3-493d-b356-5f58b66059b5)
## Network Configuration
#### paradis
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 192.238.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 192.238.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 192.238.3.1
	netmask 255.255.255.0

auto eth4
iface eth4 inet static
	address 192.238.4.1
	netmask 255.255.255.0
```
#### Armin
```
auto eth0
iface eth0 inet static
	address 192.238.2.2
	netmask 255.255.255.0
	gateway 192.238.2.1
```
#### Eren
```
auto eth0
iface eth0 inet static
	address 192.238.2.4
	netmask 255.255.255.0
	gateway 192.238.2.1
```
#### Mikasa
```
auto eth0
iface eth0 inet static
	address 192.238.2.4
	netmask 255.255.255.0
	gateway 192.238.2.1
```
#### Erwin
```
tidak ada configuration
```
#### Fritz
```
auto eth0
iface eth0 inet static
	address 192.238.4.2
	netmask 255.255.255.0
	gateway 192.238.4.1
```
#### Tybur
```
auto eth0
iface eth0 inet static
	address 192.238.4.3
	netmask 255.255.255.0
	gateway 192.238.4.1
```
#### Wathammer
```
auto eth0
iface eth0 inet static
	address 192.238.3.4
	netmask 255.255.255.0
	gateway 192.238.3.1
```
#### Colossal
```
auto eth0
iface eth0 inet static
	address 192.238.3.3
	netmask 255.255.255.0
	gateway 192.238.3.1
```
#### Beast
```
auto eth0
iface eth0 inet static
	address 192.238.3.2
	netmask 255.255.255.0
	gateway 192.238.3.1
```
#### Reiner
```
auto eth0
iface eth0 inet static
	address 192.238.1.4
	netmask 255.255.255.0
	gateway 192.238.1.1
```
#### Bertholdt
```
auto eth0
iface eth0 inet static
	address 192.238.1.3
	netmask 255.255.255.0
	gateway 192.238.1.1
```
#### Annie
```
auto eth0
iface eth0 inet static
	address 192.238.1.2
	netmask 255.255.255.0
	gateway 192.238.1.1
```
##### PREFIX PAKAI 192.238
### Node
#### Paradis
```bash
iptables -t nat -A POSTROUTING -o eth0 -j MASQUERADE -s 192.138.0.0/16
apt-get update
apt install isc-dhcp-relay -y
```
#### Tybur (DHCP)
```bash
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install isc-dhcp-server -y
```
#### Fritz (DNS)
```bash
echo 'nameserver 192.168.122.1' > /etc/resolv.conf
apt-get update
apt-get install bind9 -y
echo 'options {
directory "/var/cache/bind";
forwarders {
192.168.122.1;
};
// dnssec-validation auto;
allow-query{any;};
auth-nxdomain no;
listen-on-v6 { any; };
}; ' >/etc/bind/named.conf.options
service bind9 restart
```
#### Warhammer (Database)
```bash
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install mariadb-server -y
service mysql start
```
#### Armin (PHP)
```bash
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install nginx -y
apt-get install wget -y
apt-get install unzip -y
apt-get install lynx -y
apt-get install htop -y
apt-get install apache2-utils -y
apt-get install php7.3-fpm php7.3-common php7.3-mysql php7.3-gmp php7.3-curl php7.3-intl php7.3-mbstring php7.3-xmlrpc php7.3-gd php7.3-xml php7.3-cli php7.3-zip -y

service nginx start
service php7.3-fpm start
```
#### Mikasa (PHP)
```bash
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install nginx -y
apt-get install wget -y
apt-get install unzip -y
apt-get install lynx -y
apt-get install htop -y
apt-get install apache2-utils -y
apt-get install php7.3-fpm php7.3-common php7.3-mysql php7.3-gmp php7.3-curl php7.3-intl php7.3-mbstring php7.3-xmlrpc php7.3-gd php7.3-xml php7.3-cli php7.3-zip -y

service nginx start
service php7.3-fpm start
```
#### Eren (PHP)
```bash
echo 'nameserver 192.238.4.2' > /etc/resolv.conf
apt-get update
apt-get install nginx -y
apt-get install wget -y
apt-get install unzip -y
apt-get install lynx -y
apt-get install htop -y
apt-get install apache2-utils -y
apt-get install php7.3-fpm php7.3-common php7.3-mysql php7.3-gmp php7.3-curl php7.3-intl php7.3-mbstring php7.3-xmlrpc php7.3-gd php7.3-xml php7.3-cli php7.3-zip -y
service nginx start
service php7.3-fpm start
```
#### Annie (Laravel)
```bash
apt-get update
apt-get install lynx -y
apt-get install mariadb-client -y
apt-get install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2
apt-get install curl -y
curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
apt-get update
apt-get install php8.0-mbstring php8.0-xml php8.0-cli   php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
apt-get install nginx -y
apt-get install git -y
apt-get install htop -y
service nginx start
service php8.0-fpm start
```
#### Bertholdt (Laravel)
```bash
apt-get update
apt-get install lynx -y
apt-get install mariadb-client -y
apt-get install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2
apt-get install curl -y
curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
apt-get update
apt-get install php8.0-mbstring php8.0-xml php8.0-cli   php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
apt-get install nginx -y
apt-get install git -y
apt-get install htop -y
service nginx start
service php8.0-fpm start
```
#### Reiner (Laravel)
```bash
apt-get update
apt-get install lynx -y
apt-get install mariadb-client -y
apt-get install -y lsb-release ca-certificates apt-transport-https software-properties-common gnupg2
apt-get install curl -y
curl -sSLo /usr/share/keyrings/deb.sury.org-php.gpg https://packages.sury.org/php/apt.gpg
sh -c 'echo "deb [signed-by=/usr/share/keyrings/deb.sury.org-php.gpg] https://packages.sury.org/php/ $(lsb_release -sc) main" > /etc/apt/sources.list.d/php.list'
apt-get update
apt-get install php8.0-mbstring php8.0-xml php8.0-cli   php8.0-common php8.0-intl php8.0-opcache php8.0-readline php8.0-mysql php8.0-fpm php8.0-curl unzip wget -y
apt-get install nginx -y
apt-get install git -y
apt-get install htop -y
service nginx start
service php8.0-fpm start
```
#### Zeke (Client)
```bash
apt update
apt install lynx -y
apt install htop -y
apt install apache2-utils -y
apt-get install jq -y
```
#### Erwin (Client)
```bash
apt update
apt install lynx -y
apt install htop -y
apt install apache2-utils -y
apt-get install jq -y
```
## Soal 1
Pulau Paradis dan Marley, sama-sama menghadapi ancaman besar dari satu sama lain. Keduanya membangun infrastruktur pertahanan yang kuat untuk melindungi sistem vital mereka. Dengan strategi yang matang, mereka bersiap menghadapi serangan dan mempertahankan wilayah masing-masing.
Bangsa Marley, dipimpin oleh Zeke, telah mempersiapkan Annie, Bertholdt, dan Reiner untuk menyerang menggunakan Laravel Worker. Di sisi lain, Klan Eldia dari Paradis telah mempersiapkan Armin, Eren, dan Mikasa sebagai PHP Worker untuk mempertahankan pulau tersebut. Warhammer bertindak sebagai Database Server, sementara Beast dan Colossal sebagai Load Balancer. 
---------------------

Pulau Paradis telah menjadi tempat yang damai selama 1000 tahun, namun kedamaian tersebut tidak bertahan selamanya. Perang antara kaum Marley dan Eldia telah mencapai puncak. Kaum Marley yang dipimpin oleh Zeke, me-register domain name marley.yyy.com untuk worker Laravel mengarah pada Annie. Namun ternyata tidak hanya kaum Marley saja yang berinisiasi, kaum Eldia ternyata sudah mendaftarkan domain name eldia.yyy.com untuk worker PHP (0) mengarah pada Armin.

(1)Lakukan konfigurasi sesuai dengan peta yang sudah diberikan.

Oke, pertama saya membuat file soal1.sh di ``FRITZ``. Setelah itu saya memasukkan code berikut :
```bash
echo 'zone "marley.it10.com" { 
type master; 
file "/etc/bind/marley/marley.it10.com";
};
zone "eldia.it10.com" {
type master;
file "/etc/bind/eldia/eldia.it10.com";
}; ' >> /etc/bind/named.conf.local
mkdir /etc/bind/marley
mkdir /etc/bind/eldia
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     marley.it10.com. root.marley.it10.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      marley.it10.com.
@       IN      A       192.239.1.2     ; IP Annie' > /etc/bind/marley/marley.it10.com
echo ';
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     eldia.it10.com. root.eldia.it10.com. (
                              2         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      eldia.16.com.
@       IN      A       192.239.2.2     ; IP Armin' > /etc/bind/eldia/eldia.it10.com
service bind9 restart
```
Setelah memasukkan code tersebut, kita lanjutkan dengan bash soal1.sh
## Soal2
Jauh sebelum perang dimulai, ternyata para keluarga bangsawan, Tybur dan Fritz, telah membuat kesepakatan sebagai berikut:
Semua Client harus menggunakan konfigurasi ip address dari keluarga Tybur (dhcp).
Client yang melalui bangsa marley mendapatkan range IP dari [prefix IP].1.05 - [prefix IP].1.25 dan [prefix IP].1.50 - [prefix IP].1.100 (2)

Sama seperti diatas, kita membuat soal2.sh. Setelah itu kita masukkan dan kita jalankan code berikut:
```bash
echo 'subnet 192.238.1.0 netmask 255.255.255.0 {
    range 192.238.1.05 192.238.1.25;
    range 192.238.1.50 192.238.1.100;
    option routers 192.238.1.1;
}
subnet 192.238.2.0 netmask 255.255.255.0 {
    # Configuration for subnet 192.238.2.0
}

subnet 192.238.3.0 netmask 255.255.255.0 {
    # Configuration for subnet 192.238.3.0
}
subnet 192.238.4.0 netmask 255.255.255.0 {
    # Configuration for subnet 192.238.4.0
}' > /etc/dhcp/dhcpd.conf
# Restart DHCP service
service isc-dhcp-server restart
```
Sama seperti no. 1, kita jalankan di fritz
## Soal 3
Client yang melalui bangsa eldia mendapatkan range IP dari [prefix IP].2.09 - [prefix IP].2.27 dan [prefix IP].2 .81 - [prefix IP].2.243 (3)
Sama seperti diatas, jalankan code berikut:
```bash
echo 'subnet 192.238.1.0 netmask 255.255.255.0 {
    range 192.238.1.05 192.238.1.25;
    range 192.238.1.50 192.238.1.100;
    option routers 192.238.1.1;
}
subnet 192.238.2.1 netmask 255.255.255.0 {
    range 192.238.2.09 192.238.2.27;
    range 192.238.2.81 192.238.2.243;
    option routers 192.238.2.1;
}
subnet 192.238.3.0 netmask 255.255.255.0 {
}
subnet 192.238.4.0 netmask 255.255.255.0 {
}' > /etc/dhcp/dhcpd.conf
service isc-dhcp-server start
```
## Soal 4
Client mendapatkan DNS dari keluarga Fritz dan dapat terhubung dengan internet melalui DNS tersebut (4)

Jalankan code berikut, agar dapat tehubung ke internet dengan DNS itu
```bash
echo 'subnet 192.238.1.0 netmask 255.255.255.0 {
    range 192.238.1.05 192.238.1.25;
    range 192.238.1.50 192.238.1.100;
    option routers 192.238.1.1;
    option broadcast-address 192.238.1.255;
    option domain-name-servers 192.238.3.2;
}
subnet 192.238.2.1 netmask 255.255.255.0 {
    range 192.238.2.09 192.238.2.27;
    range 192.238.2.81 192.238.2.238;
    option routers 192.238.2.1;
    option broadcast-address 192.238.1.255;
    option domain-name-servers 192.238.3.2;
}
subnet 192.238.3.0 netmask 255.255.255.0 {
}
subnet 192.238.4.0 netmask 255.255.255.0 {
}' > /etc/dhcp/dhcpd.conf
service isc-dhcp-server start
```
## Soal 5
Dikarenakan keluarga Tybur tidak menyukai kaum eldia, maka mereka hanya meminjamkan ip address ke kaum eldia selama 6 menit. Namun untuk kaum marley, keluarga Tybur meminjamkan ip address selama 30 menit. Waktu maksimal dialokasikan untuk peminjaman alamat IP selama 87 menit. (5)

Sama Seperti soal no. 1 dan 2, jalankan di ```FRITZ```, berikut codenya :
```bash
echo 'subnet 192.238.1.0 netmask 255.255.255.0 {
range 192.238.1.05 192.238.1.25;
range 192.238.1.50 192.238.1.100;
option routers 192.238.1.1;
option broadcast-address 192.238.1.255;
option domain-name-servers 192.238.3.2;
default-lease-time 1800;
max-lease-time 5220;
}
subnet 192.238.2.1 netmask 255.255.255.0 {
range 192.238.2.09 192.238.2.27;
range 192.238.2.81 192.238.2.238;
option routers 192.238.2.1;
option broadcast-address 192.238.1.255;
option domain-name-servers 192.238.3.2;
default-lease-time 360;
max-lease-time 5220;
}
subnet 192.238.3.0 netmask 255.255.255.0 {
}
subnet 192.238.4.0 netmask 255.255.255.0 {
}' > /etc/dhcp/dhcpd.conf
service isc-dhcp-server start
```
## Soal 6
Seiring berjalannya waktu kondisi semakin memanas, untuk bersiap perang. Kaum Eldia melakukan deployment sebagai berikut
| Image |
|----|
|danielcristh0/debian-buster:1.1 atau derkora/ubuntu-jarkom-it:1.0  | 

Armin berinisiasi untuk memerintahkan setiap worker PHP untuk melakukan konfigurasi virtual host untuk website berikut https://intip.in/BangsaEldia dengan menggunakan php 7.3 (6)

jadi berikut adalah code untuk PHP:
```bash
mkdir -p /var/www/eldia.it10.com
wget --no-check-certificate 'https://drive.google.com/uc?export=download&id=1TvebIeMQjRjFURKVtA32lO9aL7U2msd6' -O /root/bangsaEldia.zip
unzip /root/bangsaEldia.zip -d /var/www/eldia.it10.com
rm -rf /root/bangsaEldia.zip
echo '
server {
        listen 80;

        root /var/www/eldia.it10.com;

        index index.php index.html index.htm;
        server_name _;

        location / {
                        try_files $uri $uri/ /index.php?$query_string;
        }

        # pass PHP scripts to FastCGI server
        location ~ \.php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
        }
location ~ /\.ht {
                        deny all;
        }
        error_log /var/log/nginx/jarkom_error.log;
        access_log /var/log/nginx/jarkom_access.log;
 }' > /etc/nginx/sites-available/eldia.it10.com

ln -s /etc/nginx/sites-available/eldia.it10.com /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default
service php7.3-fpm start
service php7.3-fpm restart
service nginx restart
nginx -t
```
Jadi diatas adalah code untuk PHP.

