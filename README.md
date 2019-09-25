# SCRIPT-SWITCH-GRUPO-6

enable
conf t
vlan 10
vlan 20
vlan 30
hostname SW-06
banner motd "ACESSO PERMITIDO PARA O GRUPO 6"
username cleiton privilege 15 secret senha6
username ruth privilege 15 secret senha6 
username guilherme privilege 15 secret senha6
username erick privilege 15 secret senha6
username vinicius privilege 15 secret senha6
line console 0
password senha6
line vty 0 15
transport input ssh
login local
exec-timeout 9
enable secret senha6
interface f0/1
switchport mode access
switchport access vlan 10
description VLAN 10
exit
interface f0/2
switchport mode access
switchport access vlan 20
description VLAN 20
exit
interface f0/3
switchport mode access
switchport access vlan 30
description VLAN 30
exit
interface vlan 10
ip address 192.168.6.129 255.255.255.192
no shutdown
interface vlan 20
ip address 192.168.6.1 255.255.255.128
no shutdown
interface vlan 30
ip address 192.168.7.1 255.255.255.240
no shutdown
interface g0/1
switchport mode trunk
switchport trunk allowed vlan 10,20,30
description PORTA TRUNK
service password-encryption
ip default-gateway 192.168.6.1
do wr
