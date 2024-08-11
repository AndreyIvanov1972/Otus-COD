


Домашнее задание
Настроите eBGP в Underlay сети, для IP связанности между всеми сетевыми устройствами.

1. Кол-во клиентов в дальнейшем неизвестно.
2. Нумерация Spine начинается с 1
3. Нумерация Leaf начинается с 1
4. Нумерация Client начинается с 1
5. Линки между Spine и Leaf - маска /30
6. Loopbak подняты на каждом узле Spine и Leaf с маской /32
7. На LEAF 1 настроены VLAN 10,20,30
8. На LEAF 2 настроены VLAN 10,20,30
9. На LEAF 3 настроены VLAN 10,20,30
10. Underlay  сеть построена на EBGP
11. Overlay сеть построена на EBGP
12. К Leaf 2 и 3 подключен маршрутизатор, имулирующий интернет
      
   


Схема адресного пространства
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/NET_8_NEW.PNG  "Схема адресного пространства")  

## 8.8.8.8 - НАШ ГУГЛ
### =============================== LEAF1 ===============================
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/LEAF1_INTERNET.PNG)
#### VLAN10
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/ping_INTERNET_VLAN10_1.PNG)
#### VLAN20
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/ping_INTERNET_VLAN20_1.PNG)

### =============================== LEAF2 ===============================
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/LEAF2_INTERNET.PNG)
#### VLAN10
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/ping_INTERNET_VLAN10_2.PNG)
#### VLAN20
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/ping_INTERNET_VLAN20_2.PNG)

###  =============================== LEAF3 ===============================
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/LEAF3_INTERNET.PNG)
#### VLAN10
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/ping_INTERNET_VLAN10_3.PNG)
#### VLAN20
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/ping_INTERNET_VLAN20_3.PNG)

##  172.16.101.0/24 - VRF PROD
###  =============================== LEAF4 ===============================

#### VRF Test1
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/Leaf4-vrf-Test1.PNG)
#### VRF PROD
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/Leaf4-vrf-PROD.PNG)
#### VLAN101
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/ping_INTERNET_VLAN_101.PNG)


## Underlay Сеть

### Spine2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_ip_bgp_summ-SPINE2.PNG)
### LEAF1
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_ip_bgp_summ-LEAF1.PNG)
### LEAF2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_ip_bgp_summ-LEAF2.PNG)
### LEAF3
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_ip_bgp_summ-LEAF3.PNG)
### LEAF4
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_ip_bgp_summ-SPINE4.PNG)

## Overlay Сеть

### Spine2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_bgp_l2vpn_evpn_summ-SPINE2.PNG)
### LEAF1
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_bgp_l2vpn_evpn_summ-LEAF1.PNG)
### LEAF2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_bgp_l2vpn_evpn_summ-LEAF2.PNG)
### LEAF3
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_bgp_l2vpn_evpn_summ-LEAF3.PNG)
### LEAF4
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/sh_bgp_l2vpn_evpn_summ-SPINE4.PNG)

## Результаты команды sh running-config

### Spine2
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/-SPINE2.txt)

### Leaf1
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/-LEAF1.txt)

### Leaf2
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/-LEAF2.txt)

### Leaf3
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/-LEAF3.txt)

### Leaf4
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ8/-LEAF4.txt)


