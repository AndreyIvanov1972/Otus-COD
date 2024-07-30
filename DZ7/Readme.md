


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
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/Net.PNG  "Схема адресного пространства")  

## Underlay Сеть
### Spine1
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Spine1%20sh%20ip%20bgp%20summ.PNG  "Sh ip bgp summary")
### Spine2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Spine2%20sh%20ip%20bgp%20summ.PNG  "Sh ip bgp summary")
### LEAF1
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Leaf1%20sh%20ip%20bgp%20summ.PNG  "Sh ip bgp summary")
### LEAF2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Leaf2%20sh%20ip%20bgp%20summ.PNG  "Sh ip bgp summary")
### LEAF3
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Leaf3%20sh%20ip%20bgp%20summ.PNG  "Sh ip bgp summary")

## Overlay Сеть
### Spine1
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Spine1%20sh%20bgp%20l2vpn%20evpn%20summ1.PNG  "Sh bgp l2 evpn summary")

### Spine2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Spine2%20sh%20bgp%20l2vpn%20evpn%20summ1.PNG "Sh bgp l2 evpn summary")
### LEAF1
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Leaf1%20sh%20bgp%20l2vpn%20evpn%20summ1.PNG "Sh bgp l2 evpn summary")
### LEAF2
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Leaf2%20sh%20bgp%20l2vpn%20evpn%20summ1.PNG "Sh bgp l2 evpn summary")
### LEAF3
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Leaf3%20sh%20bgp%20l2vpn%20evpn%20summ1.PNG "Sh bgp l2 evpn summary")

## Результаты доступности хостов в клиентских сетях

### HOST 10.1
![ХОСТ 10.1](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from10-1.txt)

### HOST 10.11
![ХОСТ 11](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from10-11.txt)

### HOST 10.2
![ХОСТ 10.2](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from10-2.txt)

### HOST 10.3
![ХОСТ 10.3](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from10-3.txt)

### HOST 20.1
![ХОСТ 20.1](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from20-1.txt)

### HOST 20.2
![ХОСТ 20.2](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from20-2.txt)

### HOST 20.3
![ХОСТ 20.3](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from20-3.txt)

### HOST 30.1
![ХОСТ 30.1](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from30-1.txt)

### HOST 30.2
![ХОСТ 30.2](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from30-2.txt)

### HOST 30.3
![ХОСТ 30.3](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ7/REZ/ping%20from30-3.txt)

## Результаты команды sh bgp l2vpn evpn

### Leaf1
![sh bgp l2vpn evpn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Leaf1%20sh%20bgp%20l2vpn%20evpn2.txt)

### Leaf2
![sh bgp l2vpn evpn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Leaf2%20sh%20bgp%20l2vpn%20evpn2.txt)

### Leaf3
![sh bgp l2vpn evpn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/Pic/Leaf3%20sh%20bgp%20l2vpn%20evpn2.txt)

## Результаты команды sh running-config

### Leaf1
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/CONF/LEAF/conf.txt)

### Leaf2
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/CONF/LEAF2/conf.txt)

### Leaf3
![Sh runn](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ6/CONF/LEAF3/conf.txt)



