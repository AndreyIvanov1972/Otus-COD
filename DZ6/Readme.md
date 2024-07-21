

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
      
   


Схема адресного пространства
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/SHEMA_SETI_LAB6.JPG  "Схема адресного пространства")  

## Underlay Сеть
### Spine1
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/SHEMA_SETI_LAB5.JPG  "Схема адресного пространства")
### Spine2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/SHEMA_SETI_LAB5.JPG  "Схема адресного пространства")
### LEAF1
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/SHEMA_SETI_LAB5.JPG  "Схема адресного пространства")
### LEAF2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/SHEMA_SETI_LAB5.JPG  "Схема адресного пространства")
### LEAF3
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/SHEMA_SETI_LAB5.JPG  "Схема адресного пространства")

## Результаты доступности хостов в клиентских сетях

### VLAN 10
![ХОСТ 10](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_10_1.txt)

![ХОСТ 11](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_10_11.txt)

![ХОСТ 2](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_10_2.txt)

![ХОСТ 3](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_10_3.txt)

### VLAN 20
![ХОСТ 11](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_20_1.txt)

![ХОСТ 2](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_20_2.txt)

![ХОСТ 3](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_20_3.txt)


### VLAN 30
![ХОСТ 11](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_30_1.txt)

![ХОСТ 2](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_30_2.txt)

![ХОСТ 3](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/VLAN_30_3.txt)


## Spine1
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/CONF/SPINE1/1.txt)

![Sh ip ospf neighbors](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/Sh%20ospf%20neighbors%3DSPINE1.txt))

![Sh bgp l2vpn evpn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn_Spine1.txt)

![Sh bgp l2vpn evpn summary](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn%20summ_Spine1.txt)

## Spine2

![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/CONF/SPINE2/1.txt)

![Sh ip ospf neighbors](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/Sh%20ospf%20neighbors%3DSPINE2.txt))

![Sh bgp l2vpn evpn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn_Spine2.txt)

![Sh bgp l2vpn evpn summary](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn%20summ_Spine2.txt)


## Leaf1
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/CONF/LEAF1/1.txt)

![Sh ip ospf neighbors](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/Sh%20ospf%20neighbors%3DLEAF1.txt))

![Sh bgp l2vpn evpn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn_LEAF1.txt)

![Sh bgp l2vpn evpn summary](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn%20%20summary_LEAF1.txt)

## Leaf2
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/CONF/LEAF2/1.txt)

![Sh ip ospf neighbors](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/Sh%20ospf%20neighbors%3DLEAF2.txt))

![Sh bgp l2vpn evpn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn_LEAF2.txt)

![Sh bgp l2vpn evpn summary](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn%20summary_LEAF2.txt)

## Leaf3
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/CONF/LEAF3/1.txt)

![Sh ip ospf neighbors](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/Sh%20ospf%20neighbors%3DLEAF3.txt))

![Sh bgp l2vpn evpn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn_LEAF3.txt)

![Sh bgp l2vpn evpn summary](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ5/REZ/sh%20bgp%20l2vpn%20evpn%20summary_LEAF3.txt)






