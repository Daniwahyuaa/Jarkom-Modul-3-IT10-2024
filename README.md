# Jarkom-Modul-3-IT10-2024
Kelompok IT 10
| No | Nama                 | NRP         |
|----|----------------------|---------------------------|
| 1  | dani Wahyu            | 5027231038                    |
| 2  | Abid Ubaidillah       | 5027231085                  | 
---
## Topology
![image](https://github.com/user-attachments/assets/459b0221-7aa3-493d-b356-5f58b66059b5)
## Network Configuration
### paradis
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
### Armin
```
auto eth0
iface eth0 inet static
	address 192.238.2.2
	netmask 255.255.255.0
	gateway 192.238.2.1
```
### Eren
```
auto eth0
iface eth0 inet static
	address 192.238.2.4
	netmask 255.255.255.0
	gateway 192.238.2.1
```
### Mikasa
```
auto eth0
iface eth0 inet static
	address 192.238.2.4
	netmask 255.255.255.0
	gateway 192.238.2.1
```
### Erwin
```
tidak ada configuration
```
### Fritz
```
auto eth0
iface eth0 inet static
	address 192.238.4.2
	netmask 255.255.255.0
	gateway 192.238.4.1
```
### Tybur
```
auto eth0
iface eth0 inet static
	address 192.238.4.3
	netmask 255.255.255.0
	gateway 192.238.4.1
```
### Wathammer
```
auto eth0
iface eth0 inet static
	address 192.238.3.4
	netmask 255.255.255.0
	gateway 192.238.3.1
```
### Colossal
```
auto eth0
iface eth0 inet static
	address 192.238.3.3
	netmask 255.255.255.0
	gateway 192.238.3.1
```
### Beast
```
auto eth0
iface eth0 inet static
	address 192.238.3.2
	netmask 255.255.255.0
	gateway 192.238.3.1
```
### Reiner
```
auto eth0
iface eth0 inet static
	address 192.238.1.4
	netmask 255.255.255.0
	gateway 192.238.1.1
```
### Bertholdt
```
auto eth0
iface eth0 inet static
	address 192.238.1.3
	netmask 255.255.255.0
	gateway 192.238.1.1
```
### Annie
```
auto eth0
iface eth0 inet static
	address 192.238.1.2
	netmask 255.255.255.0
	gateway 192.238.1.1
```
