# Jarkom-Modul-3-IT10-2024
Kelompok IT 10
| No | Nama                 | NRP         |
|----|----------------------|---------------------------|
| 1  | Dani Wahyu            | 5027231038                    |
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
apt-get update
apt-get install isc-dhcp-server -y
echo 'nameserver 192.238.4.2' >> /etc/resolv.conf
echo 'INTERFACESv4="eth0"' > /etc/default/isc-dhcp-server
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

## Soal2
Jauh sebelum perang dimulai, ternyata para keluarga bangsawan, Tybur dan Fritz, telah membuat kesepakatan sebagai berikut:
Semua Client harus menggunakan konfigurasi ip address dari keluarga Tybur (dhcp).
Client yang melalui bangsa marley mendapatkan range IP dari [prefix IP].1.05 - [prefix IP].1.25 dan [prefix IP].1.50 - [prefix IP].1.100 (2)

Kita membuat soal2.sh. Setelah itu kita masukkan dan kita jalankan code berikut:
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
untuk di tybur
```bash
    range 192.238.1.05 192.238.1.25;
    range 192.238.1.50 192.238.1.100;
    option routers 192.238.1.1;
```
Kita jalankan di fritz
## Soal 3
Client yang melalui bangsa eldia mendapatkan range IP dari [prefix IP].2.09 - [prefix IP].2.27 dan [prefix IP].2 .81 - [prefix IP].2.243 (3)
Sama seperti diatas, jalankan code berikut:
untuk di tybur
```bash
    range 192.238.2.09 192.238.2.27;
    range 192.238.2.81 192.238.2.243;
    option routers 192.238.2.1;
```
untuk di Fritz
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

mkdir -p /var/www/eldia.it10.com

wget --no-check-certificate 'https://drive.google.com/drive/folders/1MHVQDEjHbOw1HkdhjwHwzjX9KNA8AgVn?usp=sharing' -O /root/bangsaEldia.zip
unzip /root/bangsaEldia.zip -d /var/www/eldia.it10.com
rm -rf /root/bangsaEldia.zip

echo '
server {

        listen 80;

        root /var/www/eldia.it10.com;

        index index.php index.html index.htm;
        servername ;

        location / {
                        try_files $uri $uri/ /index.php?$query_string;
        }

        # pass PHP scripts to FastCGI server
        location ~ .php$ {
        include snippets/fastcgi-php.conf;
        fastcgi_pass unix:/var/run/php/php7.3-fpm.sock;
        }

location ~ /.ht {
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

## Soal 7
Dikarenakan Armin sudah mendapatkan kekuatan titan colossal, maka bantulah kaum eldia menggunakan colossal agar dapat bekerja sama dengan baik. Kemudian lakukan testing dengan 6000 request dan 200 request/second. (7)

##### soal7col.sh
```bash
echo '
upstream myweb  {
server 192.238.2.2; #IP Armin
server 192.238.2.3; #IP Eren
server 192.238.2.1; #IP Mikasa
 }
 server {
listen 80;
server_name eldia.10.com;
location / {
proxy_pass http://myweb; }
}' > /etc/nginx/sites-available/lb-php
ln -s /etc/nginx/sites-available/lb-php /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default
service nginx restart
nginx -t
```
##### soal7fritz.sh
```bash
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
@       IN      NS      eldia.it10.com.
@       IN      A       192.238.3.3     ; IP Colossal' > /etc/bind/eldia/eldia.it10.com
service bind9 restart
```
kemudian dilakukan testing dengan cara memasukkan 
```bash
ab -n 6000 -c 200 http://eldia.it10.com/
```

## Soal 8
Karena Erwin meminta “laporan kerja Armin”, maka dari itu buatlah analisis hasil testing dengan 1000 request dan 75 request/second untuk masing-masing algoritma Load Balancer dengan ketentuan sebagai berikut:
Nama Algoritma Load Balancer
Report hasil testing pada Apache Benchmark
Grafik request per second untuk masing masing algoritma. 
Analisis (8)

Cara testing load balancer yaitu dengan cara memasukkan code sebagai berikut
```bash
echo 'upstream round_robin  {
    server 192.238.2.2 ; #IP Armin
    server 192.238.2.3 ; #IP Eren
    server 192.238.2.4 ; #IP Mikasa
}
server {
    listen 8080;
    location / {
    proxy_pass http://round_robin;
    proxy_set_header    X-Real-IP $remote_addr;
    proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header    Host $http_host;
    }
    error_log /var/log/nginx/lb_error.log;
    access_log /var/log/nginx/lb_access.log;
}' >/etc/nginx/sites-available/round-robin
echo 'upstream generic_hash  {
    hash $request_uri consistent;
    server 192.238.2.2 ; #IP Armin
    server 192.238.2.3 ; #IP Eren
    server 192.238.2.4 ; #IP Mikasa
}

server {
    listen 8081;
    location / {
    proxy_pass http://generic_hash;
    proxy_set_header    X-Real-IP $remote_addr;
    proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header    Host $http_host;
    }
    error_log /var/log/nginx/lb_error.log;
    access_log /var/log/nginx/lb_access.log;
}' >/etc/nginx/sites-available/generic-hash
echo 'upstream ip_hash  {
    ip_hash;
    server 192.238.2.2 ; #IP Armin
    server 192.238.2.3 ; #IP Eren
    server 192.238.2.4 ; #IP Mikasa
}
server {
    listen 8082;
    location / {
    proxy_pass http://ip_hash;
    proxy_set_header    X-Real-IP $remote_addr;
    proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header    Host $http_host;
    }
    error_log /var/log/nginx/lb_error.log;
    access_log /var/log/nginx/lb_access.log;
}' >/etc/nginx/sites-available/ip-hash
echo 'upstream least_conn  {
    least_conn;
    server 192.238.2.2 ; #IP Armin
    server 192.238.2.3 ; #IP Eren
    server 192.238.2.4 ; #IP Mikasa
}
server {
    listen 8083;  
    location / {
    proxy_pass http://least_conn;
    proxy_set_header    X-Real-IP $remote_addr;
    proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
    proxy_set_header    Host $http_host;
    }
    error_log /var/log/nginx/lb_error.log;
    access_log /var/log/nginx/lb_access.log;
}' >/etc/nginx/sites-available/least-conn
unlink /etc/nginx/sites-enabled/default
ln -s /etc/nginx/sites-available/round-robin /etc/nginx/sites-enabled/round-robin
ln -s /etc/nginx/sites-available/generic-hash /etc/nginx/sites-enabled/generic-hash
ln -s /etc/nginx/sites-available/ip-hash /etc/nginx/sites-enabled/ip-hash
ln -s /etc/nginx/sites-available/least-conn /etc/nginx/sites-enabled/least-conn
service nginx restart
```
tidak lupa membuat laporan dengan cara memasukkan code sebagai berikut:
```bash
#!/bin/bash
LB_ADDR="192.243.4.3"
RR_IP="8080"   
IPH_IP="8082"   
GENH_IP="8081" 
LC3W_IP="8083"  
LC2W_IP="8004"  
LC1W_IP="8005"  
mkdir -p /root/report
RoundRobinTest() {
  AMT=$1
  CON=$2

  echo "$(ab -n $AMT -c $CON http:\/\/$LB_ADDR:$RR_IP\/)" > /root/report/round_robin_test.bin
  echo "Round Robin Test Done"
}

IPHashTest() {
  AMT=$1
  CON=$2

  echo "$(ab -n $AMT -c $CON http:\/\/$LB_ADDR:$IPH_IP\/)" > /root/report/ip_hash_test.bin
  echo "IP Hash Test Done"
}

GenHashTest() {
  AMT=$1
  CON=$2

  echo "$(ab -n $AMT -c $CON http:\/\/$LB_ADDR:$GENH_IP\/)" > /root/report/gen_hash_test.bin
  echo "Generic Hash Test Done"
}

LeastConn3Test() {
  AMT=$1
  CON=$2

  echo "$(ab -n $AMT -c $CON http:\/\/$LB_ADDR:$LC3W_IP\/)" > /root/report/least_conn_3_test.bin
  echo "Least Connection with 3 Workers Test Done"
}

LeastConn2Test() {
  AMT=$1
  CON=$2

  echo "$(ab -n $AMT -c $CON http:\/\/$LB_ADDR:$LC2W_IP\/)" > /root/report/least_conn_2_test.bin
  echo "Least Connection with 2 Workers Test Done"
}

LeastConn1Test() {
  AMT=$1
  CON=$2

  echo "$(ab -n $AMT -c $CON http:\/\/$LB_ADDR:$LC1W_IP\/)" > /root/report/least_conn_1_test.bin
  echo "Least Connection with 1 Worker Test Done"
}

SingleTest() {
  echo "
========== Single Test ==========

Pilih Load Balancer:

1.) Round Robin - 3 Workers
2.) IP Hash - 3 Workers
3.) Generic Hash - 3 Workers
4.) Least Connection - 3 Workers
5.) Least Connection - 2 Workers
6.) Least Connection - 1 Workers
"

  echo -n "Pilih Opsi Pengujian: "
  read optLB

  if [ $optLB -eq 1 ];
  then
    echo -n "Masukkan Jumlah Request: "
    read inReq
    echo -n "Masukkan Jumlah Concurrency: "
    read inCon

    RoundRobinTest $inReq $inCon

    echo -e "\n\n+++++ Laporan Hasil Pengujian Load Balancer +++++"
    echo -e "\nKeterangan Pengujian"
    echo -e "Nama Load Balancer: \t Round Robin"
    echo -e "Jumlah Worker: \t\t 3 Workers"

    echo -e "\nTabel Hasil\n"
 
    echo -e "Load Balancer\tWorker(s)\tReq per second\tComplete req\tFailed req\tTime per req\tTransfer rate"


    awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Round Robin\t3\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/round_robin_test.bin
    echo -e "\n\n+++++ Akhir Laporan +++++\n"
  elif [ $optLB -eq 2 ]; then
    echo -n "Masukkan Jumlah Request: "
    read inReq
    echo -n "Masukkan Jumlah Concurrency: "
    read inCon

    IPHashTest $inReq $inCon

    echo -e "\n\n+++++ Laporan Hasil Pengujian Load Balancer +++++"
    echo -e "\nKeterangan Pengujian"
    echo -e "Nama Load Balancer: \t IP Hash"
    echo -e "Jumlah Worker: \t\t 3 Workers"

    echo -e "\nTabel Hasil\n"
 
    echo -e "Load Balancer\tWorker(s)\tReq per second\tComplete req\tFailed req\tTime per req\tTransfer rate"
    awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "IP Hash\t\t3\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/ip_hash_test.bin
    echo -e "\n\n+++++ Akhir Laporan +++++\n"
  elif [ $optLB -eq 3 ]; then
    echo -n "Masukkan Jumlah Request: "
    read inReq
    echo -n "Masukkan Jumlah Concurrency: "
    read inCon
    GenHashTest $inReq $inCon
    echo -e "\n\n+++++ Laporan Hasil Pengujian Load Balancer +++++"
    echo -e "\nKeterangan Pengujian"
    echo -e "Nama Load Balancer: \t Generic Hash"
    echo -e "Jumlah Worker: \t\t 3 Workers"
    echo -e "\nTabel Hasil\n"
    echo -e "Load Balancer\tWorker(s)\tReq per second\tComplete req\tFailed req\tTime per req\tTransfer rate"
    awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Generic Hash\t3\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/gen_hash_test.bin
    echo -e "\n\n+++++ Akhir Laporan +++++\n"
  elif [ $optLB -eq 4 ]; then
    echo -n "Masukkan Jumlah Request: "
    read inReq
    echo -n "Masukkan Jumlah Concurrency: "
    read inCon
    LeastConn3Test $inReq $inCon
    echo -e "\n\n+++++ Laporan Hasil Pengujian Load Balancer +++++"
    echo -e "\nKeterangan Pengujian"
    echo -e "Nama Load Balancer: \t Least Connection"
    echo -e "Jumlah Worker: \t\t 3 Workers"
    echo -e "\nTabel Hasil\n"
    echo -e "Load Balancer\tWorker(s)\tReq per second\tComplete req\tFailed req\tTime per req\tTransfer rate"
    awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Least Conn\t3\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/least_conn_3_test.bin
    echo -e "\n\n+++++ Akhir Laporan +++++\n"
  elif [ $optLB -eq 5 ]; then
    echo -n "Masukkan Jumlah Request: "
    read inReq
    echo -n "Masukkan Jumlah Concurrency: "
    read inCon
    LeastConn2Test $inReq $inCon
    echo -e "\n\n+++++ Laporan Hasil Pengujian Load Balancer +++++"
    echo -e "\nKeterangan Pengujian"
    echo -e "Nama Load Balancer: \t Least Connection"
    echo -e "Jumlah Worker: \t\t 2 Workers"
    echo -e "\nTabel Hasil\n"
    echo -e "Load Balancer\tWorker(s)\tReq per second\tComplete req\tFailed req\tTime per req\tTransfer rate"
    awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Least Conn\t2\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/least_conn_2_test.bin
    echo -e "\n\n+++++ Akhir Laporan +++++\n"
  elif [ $optLB -eq 6 ]; then
    echo -n "Masukkan Jumlah Request: "
    read inReq
    echo -n "Masukkan Jumlah Concurrency: "
    read inCon
    LeastConn1Test $inReq $inCon
    echo -e "\n\n+++++ Laporan Hasil Pengujian Load Balancer +++++"
    echo -e "\nKeterangan Pengujian"
    echo -e "Nama Load Balancer: \t LEast Connection"
    echo -e "Jumlah Worker: \t\t 1 Workers"
    echo -e "\nTabel Hasil\n
    echo -e "Load Balancer\tWorker(s)\tReq per second\tComplete req\tFailed req\tTime per req\tTransfer rate"
    awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Least Conn\t1\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/least_conn_1_test.bin
    echo -e "\n\n+++++ Akhir Laporan +++++\n"
  else
    echo "Unknown Input"
  fi
}
MultiTestLB() {
  echo "
========== Multi Test - By LB Method ==========

"
  echo -n "Masukkan Jumlah Request: "
  read inReq
  echo -n "Masukkan Jumlah Concurrency: "
  read inCon
  RoundRobinTest $inReq $inCon
  sleep 1
  IPHashTest $inReq $inCon
  sleep 1
  GenHashTest $inReq $inCon
  sleep 1
  LeastConn3Test $inReq $inCon
  echo "Multi Test Done"
  echo -e "\n\n+++++ Laporan Hasil Pengujian Load Balancer +++++"
  echo -e "\nKeterangan Pengujian"
  echo -e "Nama Load Balancer: \t Round Robin, Least Connection, IP Hash, dan Generic Hash"
  echo -e "Jumlah Worker: \t\t 3 Workers"
  echo -e "\nTabel Hasil\n"
  echo -e "Load Balancer\tWorker(s)\tReq per second\tComplete req\tFailed req\tTime per req\tTransfer rate"
  awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Round Robin\t3\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/round_robin_test.bin
  awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Least Conn\t3\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/least_conn_3_test.bin
  awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "IP Hash\t\t3\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/ip_hash_test.bin
  awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Generic Hash\t3\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/gen_hash_test.bin
  echo -e "\n\n+++++ Akhir Laporan +++++\n"
}
MultiTestWorker() {
  echo "
========== Multi Test - By Worker Amount ==========

"

  echo -n "Masukkan Jumlah Request: "
  read inReq
  echo -n "Masukkan Jumlah Concurrency: "
  read inCon
  LeastConn3Test $inReq $inCon
  sleep 1
  LeastConn2Test $inReq $inCon
  sleep 1
  LeastConn1Test $inReq $inCon
  sleep 1
  echo "Multi Test Done"
  echo -e "\n\n+++++ Laporan Hasil Pengujian Load Balancer +++++"
  echo -e "\nKeterangan Pengujian"
  echo -e "Nama Load Balancer: \t Round Robin, Least Connection, IP Hash, dan Generic Hash"
  echo -e "Jumlah Worker: \t\t 3 Workers"

  echo -e "\nTabel Hasil\n"
  echo -e "Load Balancer\tWorker(s)\tReq per second\tComplete req\tFailed req\tTime per req\tTransfer rate"\
  awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Least Conn\t3\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/least_conn_3_test.bin
  awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Least Conn\t2\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/least_conn_2_test.bin
  awk '/Requests per second/{req_sec=$(NF-2)} /Complete requests/{comp_req=$NF} /Failed requests/{fail_req=$NF} /Time per request/{time_req=$(NF-6)} /Transfer rate/{transfer_rate=$(NF-2)} END {printf "Least Conn\t1\t\t%s\t\t%s\t\t%s\t\t%s\t\t%s\n", req_sec, comp_req, fail_req, time_req, transfer_rate}' /root/report/least_conn_1_test.bin
  echo -e "\n\n+++++ Akhir Laporan +++++\n"
}

echo "
========== Apache Benchmarking ==========
          Dibuat oleh Jarkom-IT10

Opsi Pengujian Load Balancer:

1.) Single Test
2.) Multi Test - By LB Method
3.) Multi Test - By Worker Amount

"

echo -n "Pilih Opsi Pengujian: "
read optLB

if [ $optLB -eq 1 ];
then
  SingleTest
elif [ $optLB -eq 2 ]; then
  MultiTestLB
elif [ $optLB -eq 3 ]; then
  MultiTestWorker
else
  echo "Unknown Input"
fi
```
setelah ini kita akan mendapatkan semua laporan.

## Soal 9
Dengan menggunakan algoritma Least-Connection, lakukan testing dengan menggunakan 3 worker, 2 worker, dan 1 worker sebanyak 1000 request dengan 10 request/second, kemudian tambahkan grafiknya pada “laporan kerja Armin”. (9)

kita buat file sh nya terlebih dahulu
```bash
echo 'upstream least_conn_2_worker  {
    least_conn;
    server 192.238.2.2 ; #IP Armin
    server 192.238.2.3 ; #IP Eren
}
server {
    listen 8084;
        location / {
            proxy_pass http://least_conn_2_worker;
            proxy_set_header    X-Real-IP $remote_addr;
            proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header    Host $http_host;
        }
    error_log /var/log/nginx/lb_error.log;
    access_log /var/log/nginx/lb_access.log;
}' >/etc/nginx/sites-available/least-conn-2-worker
echo 'upstream least_conn_1_worker  {
    least_conn;
    server 192.238.2.2 ; #IP Armin
}
server {
    listen 8085;
        location / {
            proxy_pass http://least_conn_1_worker;
            proxy_set_header    X-Real-IP $remote_addr;
            proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header    Host $http_host;
        }
    error_log /var/log/nginx/lb_error.log;
    access_log /var/log/nginx/lb_access.log;
}' >/etc/nginx/sites-available/least-conn-1-worker
ln -s /etc/nginx/sites-available/least-conn-2-worker /etc/nginx/sites-enabled/least-conn-2-worker
ln -s /etc/nginx/sites-available/least-conn-1-worker /etc/nginx/sites-enabled/least-conn-1-worker
service nginx restart
```
## Soal 10
Selanjutnya coba tambahkan keamanan dengan konfigurasi autentikasi di Colossal dengan dengan kombinasi username: “arminannie” dan password: “jrkmyyy”, dengan yyy merupakan kode kelompok. Terakhir simpan file “htpasswd” nya di /etc/nginx/supersecret/ (10)

Kita tambahkan keamanan dengan menjalankan code berikut:
```bash
mkdir /etc/nginx/supersecret/
htpasswd -bc /etc/nginx/supersecret/htpasswd arminannie jrkmit10
echo 'upstream round_robin  {
    server 192.238.2.2 ; #IP Armin
    server 192.238.2.3 ; #IP Eren
    server 192.238.2.4 ; #IP Mikasa
}
server {
    listen 8080;
        location / {
            auth_basic "Restricted Content";
            auth_basic_user_file /etc/nginx/supersecret/htpasswd;
            proxy_pass http://round_robin;
            proxy_set_header    X-Real-IP $remote_addr;
            proxy_set_header    X-Forwarded-For $proxy_add_x_forwarded_for;
            proxy_set_header    Host $http_host;
        }
    error_log /var/log/nginx/lb_error.log;
    access_log /var/log/nginx/lb_access.log;
}' >/etc/nginx/sites-available/round-robin
ln -s /etc/nginx/sites-available/round-robin /etc/nginx/sites-enabled/round-robin
service nginx restart
```
## Soal 11
Lalu buat untuk setiap request yang mengandung /titan akan di proxy passing menuju halaman https://attackontitan.fandom.com/wiki/Attack_on_Titan_Wiki (11) 
hint: (proxy_pass)

Code dibawah dapat kita jalankan
```bash
#Pada Colossal
echo '
 upstream myweb  {
        least_conn;
        server 192.238.2.2; #IP Armin
        server 192.238.2.3; #IP Eren
        server 192.238.2.4; #IP Mikasa
 }
 server {
        listen 80;
        server_name eldia.10.com;
        location / {
        auth_basic "Restricted Access";
        auth_basic_user_file /etc/nginx/supersecret/htpasswd;
        proxy_pass http://myweb;
        }
        location /titan/ {
        proxy_pass https://attackontitan.fandom.com/wiki/Attack_on_Titan_Wiki/;
        }
 }' > /etc/nginx/sites-available/lb-php
ln -s /etc/nginx/sites-available/lb-php /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default
service nginx restart
nginx -t
```
## Soal 12
Selanjutnya Colossal ini hanya boleh diakses oleh client dengan IP [Prefix IP].1.77, [Prefix IP].1.88, [Prefix IP].2.144, dan [Prefix IP].2.156. (12) 
hint: (fixed in dulu clientnya)

Kita masukkan 3 code yang masing" ada di Tybur, Zeke, Dan Colossal
##### code untuk tybur
```bash
echo 'host Zeke{
        hardware ethernet fa:61:fb:1a:8d:5b;
        fixed-address 192.238.1.77;
		}
' >> /etc/dhcp/dhcpd.conf
service isc-dhcp-server restart
```
##### code untuk Zeke
```bash
echo 'hwaddress ether fa:61:fb:1a:8d:5b' >> /etc/network/interfaces
```
##### code untuk colossal
```bash
echo '
 upstream myweb  {
        least_conn;
        server 192.238.2.2; #IP Armin
        server 192.238.2.3; #IP Eren
        server 192.238.2.4; #IP Mikasa
		 }

server {
	listen 80;
	server_name eldia.10.com;

	location / {
		allow 192.238.1.77;
		allow 192.238.1.88;
		allow 192.238.2.144;
		allow 192.238.2.156;
		deny all;

		auth_basic "Restricted Content";
		auth_basic_user_file /etc/nginx/supersecret/htpasswd;
		proxy_pass http://myweb;
	}

	location /dune {
		proxy_pass https://attackontitan.fandom.com/wiki/Attack_on_Titan_Wiki/;
	}
}' > /etc/nginx/sites-available/lb-php

ln -s /etc/nginx/sites-available/lb-php /etc/nginx/sites-enabled
rm -rf /etc/nginx/sites-enabled/default

service nginx restart
nginx -t
```
## Soal 13
Melihat perlawanan yang sengit dari kaum eldia, kaum marley pun memutar otak dan mengatur para worker di marley. 
Karena mengetahui bahwa ada keturunan marley yang mewarisi kekuatan titan, Zeke pun berinisiatif untuk menyimpan data data penting di Warhammer, dan semua data tersebut harus dapat diakses oleh anak buah kesayangannya, Annie, Reiner, dan Berthold.  (13)

kita bisa memasukkan code dibawah
```bash
mysql -u root -p
CREATE USER 'kelompokit10'@'%' IDENTIFIED BY 'passwordit10';
CREATE USER 'kelompokit10'@'localhost' IDENTIFIED BY 'passwordit10';
CREATE DATABASE dbkelompokit10;
GRANT ALL PRIVILEGES ON *.* TO 'kelompokit10'@'%';
GRANT ALL PRIVILEGES ON *.* TO 'kelompokit10'@'localhost';
FLUSH PRIVILEGES;
exit
```
akses semua laravel dengan menggunakan
```bash
mariadb --host=192.238.3.4 --port=3306 --user=kelompokit10 --password
```
