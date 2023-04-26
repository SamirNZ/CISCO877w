# Tutoriel config CISCO877w

## Introduction
Dans ce tutoriel nous avons montré comment réaliser un configuration basique d'un routeur CISCO 877w 

# reset
```
write erase
reload
[yes/no]: n
```
# Change mot de pass session pour telnet
```
hostname Router_name
enable pass cisco
line vty 0 4
pass cisco
login
exi
do wr
en 
conf t
do sh ip int br
int Dot11Radio0
do sh run int Dot11Radio0
ssid yourSSID
encryption vlan 1 mode ciphers tkip aes-ccm
exi
int Dot11Radio0.1
encapsulation dot1Q 1 native
bridge-group 1
do sh run int Dot11Radio0.1
exi
int vlan 1
no ip address
no shut
bridge-group 1
exi
int dot11Radio 0
no shu
exi
bridge irb
int bVI 1
ip address 10.67.10.1 255.255.255.0
exi
dot11 ssid yourSSID
vlan 1
authentification open
authentification key-management wpa
guest-mode
wpa-psk ascii 0 yourPassword
exi
dot11Radio 0
channeel least-congested
do sh dot11 as
exi
ip dhcp pool yourSSID
network 10.67.19.0 255.255.255.0
ip dhcp excluded-address 10.67.19.1 10.67.19.10
bridge 1 route ip
exi
service dhcp
sh dot11 as
```
