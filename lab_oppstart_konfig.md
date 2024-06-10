hostname IOS-switch-1
aaa new-model
username autom8 privilege 15 password 0 alt
line 0 4
privilege level 15

cdp run
vlan 170
interface Vlan170
 ip address 10.170.0.231 255.255.255.0
 no shut
 
ip route 0.0.0.0 0.0.0.0 10.170.0.1

interface GigabitEthernet0/0
 switchport access vlan 170
 switchport mode access
 
interface GigabitEthernet0/1
 no negotiation auto
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable
 
interface GigabitEthernet0/2
 no negotiation auto
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable
 
interface GigabitEthernet0/2
 no negotiation auto
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable 

interface GigabitEthernet0/3
 no negotiation auto
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable 

_______________________________________________________________


hostname IOS-switch-2
aaa new-model
username autom8 privilege 15 password 0 alt
line 0 4
privilege level 15

cdp run
vlan 170
name vlan170
interface Vlan170
 ip address 10.170.0.232 255.255.255.0
 no shut
 
ip route 0.0.0.0 0.0.0.0 10.170.0.1

 
interface GigabitEthernet0/0
 no negotiation auto
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable
 
interface GigabitEthernet0/1
 no negotiation auto
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable

interface GigabitEthernet0/2
 no negotiation auto
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable 

interface GigabitEthernet0/3
 no negotiation auto
 switchport trunk encapsulation dot1q
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable 
_______________________________________________________________


hostname IOS-XE-switch-3
aaa new-model
username autom8 privilege 15 password 0 alt
line 0 4
privilege level 15
cdp run
vlan 170
name vlan170
interface Vlan170
 ip address 10.170.0.233 255.255.255.0
 no shut
 
ip default-gateway 10.170.0.1

 
interface G1/0/1
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable
 
interface G1/0/2
 switchport access vlan 170
 switchport mode access
 cdp enable

interface G1/0/3
 switchport access vlan 170
 switchport mode access
 cdp enable

interface G1/0/4
 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable

 
_______________________________________________________________

hostname IOS-XE-switch-4
aaa new-model
username autom8 privilege 15 password 0 alt
line 0 4
privilege level 15
cdp run
vlan 170
name vlan170
interface Vlan170
 ip address 10.170.0.234 255.255.255.0
 no shut
 
ip default-gateway 10.170.0.1

 
interface G1/0/1

 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable
 
interface G1/0/2
 switchport access vlan 170
 switchport mode access
 cdp enable

interface G1/0/3

 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable

interface G1/0/4

 switchport trunk allowed vlan 170
 switchport mode trunk
 cdp enable
 
_______________________________________________________________


hostname IOS-ruter-1
aaa new-model
username autom8 privilege 15 password 0 alt
ip domain-name autom8.no
crypto key generate rsa modulus 4096
ip ssh version 2
line vty 0 4
 privilege level 15
 login authentication local
 transport input ssh
ip route 0.0.0.0 0.0.0.0 10.170.0.1
cdp run
int g0/0
no shut
ip address 10.170.0.251 255.255.255.0

_______________________________________________________________


hostname IOS-XE-ruter-2
username autom8 privilege 15 password 0 alt
line vty 0 4
 privilege level 15
 login local
 transport input ssh
ip route 0.0.0.0 0.0.0.0 10.170.0.1
cdp run
int GigabitEthernet1
no shut
ip address 10.170.0.252 255.255.255.0

_______________________________________________________________

hostname IOS-XE-ruter-3
cdp run
int GigabitEthernet1
no shut
ip address 10.170.0.253 255.255.255.0