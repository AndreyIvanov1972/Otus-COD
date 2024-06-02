
Домашнее задание
Проектирование адресного пространства и построение сети ЦОД на ISIS

Допущения и предположения
1. На момент проектирования - есть только один ЦОД.
2. Кол-во клиентов в дальнейшем неизвестно.
3. Нумерация Spine начинается с 1
4. Нумерация Leaf начинается с 1
5. Нумерация Client начинается с 1
6. Линки между Spine и Leaf - маска /30
7. Линки между Leaf и Client  - маска /24
8. Формат адреса между Spine и Leaf  
         10.__Spine__.__Leaf__.0/30
9. Формат адреса между Leaf и Client  
         172.16.__Leaf__.__Client__/24  
10. Loopbak подняты на каждом узле Spine и Leaf с маской /32
11. Формат адреса Loopback  
          10.__Spine__.0.1/32  
          10.0.__Leaf__.1/3
12. Добавлен уровень SuperSpine, состоящий из одного узла.
13. SuperSpine имеет Lo0 - 10.10.10.10/32
14. Формат адреса между SuperSpine и Spine.
          10.10.__Spine__.0/30
Проблемы связанные с расширением - если будет добавлен новый ЦОД, то нумерация новых Spine и Leaf может начинаться с 50 или 100, 
в зависимости от кол-ва узлов в первом ЦОДе.  

__LoopBack не используем для построения связностей. Не используем unnumbered hosts.__

Схема адресного пространства
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2/dz2-shema%20seti-1.JPG  "Схема адресного пространства")  

Таблица коммутации  
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2/HostConnectionTable.JPG)


## SuperSpine 
### ISIS Adjacency
SS# sh isis adjacency
IS-IS process: Underlay VRF: default
IS-IS adjacency database:
Legend: '!': No AF level connectivity in given topology
System ID       SNPA            Level  State  Hold Time  Interface
SPINE2          N/A             1-2    UP     00:00:28   Ethernet1/3
SPINE1          N/A             1-2    UP     00:00:23   Ethernet1/4

### ISIS Database
SS# sh isis database
IS-IS Process: Underlay LSP database VRF: default
IS-IS Level-1 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x0000000F   0x0E29    1131       0/0/0/3
  LEAF2.00-00           0x000001BE   0x501F    1192       0/0/0/3
  SPINE1.00-00          0x0000000E   0xD179    745        0/0/0/3
  SPINE2.00-00          0x0000000F   0x320F    672        0/0/0/3
  SS.00-00            * 0x0000000C   0xC8A7    1150       0/0/0/3

IS-IS Level-2 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x0000000F   0x0E29    1052       0/0/0/3
  LEAF2.00-00           0x000001BE   0x501F    1197       0/0/0/3
  SPINE1.00-00          0x0000000E   0xD179    753        0/0/0/3
  SPINE2.00-00          0x0000000F   0x320F    703        0/0/0/3
  SS.00-00            * 0x0000000C   0xC8A7    1006       0/0/0/3

### Резултаты ping по всем узлам сети

SS# ping 10.10.10.10 count 2
PING 10.10.10.10 (10.10.10.10): 56 data bytes
64 bytes from 10.10.10.10: icmp_seq=0 ttl=255 time=17.766 ms
64 bytes from 10.10.10.10: icmp_seq=1 ttl=255 time=0.848 ms

--- 10.10.10.10 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 0.848/9.306/17.766 ms
SS# ping 10.1.0.1 count 2
PING 10.1.0.1 (10.1.0.1): 56 data bytes
64 bytes from 10.1.0.1: icmp_seq=0 ttl=254 time=70.158 ms
64 bytes from 10.1.0.1: icmp_seq=1 ttl=254 time=38.201 ms

--- 10.1.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 38.201/54.179/70.158 ms
SS# ping 10.2.0.1 count 2
PING 10.2.0.1 (10.2.0.1): 56 data bytes
64 bytes from 10.2.0.1: icmp_seq=0 ttl=254 time=38.732 ms
64 bytes from 10.2.0.1: icmp_seq=1 ttl=254 time=27.955 ms

--- 10.2.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 27.955/33.343/38.732 ms
SS# ping 10.0.1.1 count 2
PING 10.0.1.1 (10.0.1.1): 56 data bytes
64 bytes from 10.0.1.1: icmp_seq=0 ttl=253 time=76.479 ms
64 bytes from 10.0.1.1: icmp_seq=1 ttl=253 time=35.222 ms

--- 10.0.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 35.222/55.85/76.479 ms
SS# ping 10.0.2.1 count 2
PING 10.0.2.1 (10.0.2.1): 56 data bytes
64 bytes from 10.0.2.1: icmp_seq=0 ttl=253 time=114.768 ms
64 bytes from 10.0.2.1: icmp_seq=1 ttl=253 time=19.085 ms

--- 10.0.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 19.085/66.926/114.768 ms
SS# ping 10.0.3.1 count 2
PING 10.0.3.1 (10.0.3.1): 56 data bytes
64 bytes from 10.0.3.1: icmp_seq=0 ttl=253 time=37.446 ms
64 bytes from 10.0.3.1: icmp_seq=1 ttl=253 time=15.141 ms

--- 10.0.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 15.141/26.293/37.446 ms
SS# ping 172.16.1.1 count 2
PING 172.16.1.1 (172.16.1.1): 56 data bytes
64 bytes from 172.16.1.1: icmp_seq=0 ttl=61 time=149.57 ms
64 bytes from 172.16.1.1: icmp_seq=1 ttl=61 time=27.139 ms

--- 172.16.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 27.139/88.354/149.57 ms
SS# ping 172.16.2.1 count 2
PING 172.16.2.1 (172.16.2.1): 56 data bytes
64 bytes from 172.16.2.1: icmp_seq=0 ttl=61 time=35.125 ms
64 bytes from 172.16.2.1: icmp_seq=1 ttl=61 time=17.498 ms

--- 172.16.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 17.498/26.311/35.125 ms
SS# ping 172.16.3.1 count 2
PING 172.16.3.1 (172.16.3.1): 56 data bytes
64 bytes from 172.16.3.1: icmp_seq=0 ttl=61 time=48.376 ms
64 bytes from 172.16.3.1: icmp_seq=1 ttl=61 time=18.746 ms

--- 172.16.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 18.746/33.56/48.376 ms
SS# ping 172.16.4.1 count 2
PING 172.16.4.1 (172.16.4.1): 56 data bytes
64 bytes from 172.16.4.1: icmp_seq=0 ttl=61 time=53.402 ms
64 bytes from 172.16.4.1: icmp_seq=1 ttl=61 time=35.506 ms

--- 172.16.4.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 35.506/44.454/53.402 ms
SS#

## Spine1 
### ISIS Adjacency
SPINE1(config-if)# sh isis adjacency
IS-IS process: Underlay VRF: default
IS-IS adjacency database:
Legend: '!': No AF level connectivity in given topology
System ID       SNPA            Level  State  Hold Time  Interface
LEAF1           N/A             1-2    UP     00:00:24   Ethernet1/1
LEAF2           N/A             1-2    UP     00:00:28   Ethernet1/2
LEAF2           N/A             1-2    LOST   00:00:01   Ethernet1/3
LEAF3           N/A             1-2    UP     00:00:33   Ethernet1/3
SS              N/A             1-2    UP     00:00:28   Ethernet1/4

### ISIS Database
SPINE1(config-if)# sh isis database
IS-IS Process: Underlay LSP database VRF: default
IS-IS Level-1 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x00000012   0x082C    986        0/0/0/3
  LEAF2.00-00           0x00000302   0xEE3B    810        0/0/0/3
  LEAF3.00-00           0x00000001   0x28E5    827        0/0/0/3
  SPINE1.00-00        * 0x00000013   0x1A1C    850        0/0/0/3
  SPINE2.00-00          0x00000014   0x7AB1    849        0/0/0/3
  SS.00-00              0x0000000F   0xC2AA    1100       0/0/0/3

IS-IS Level-2 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x00000012   0x082C    900        0/0/0/3
  LEAF2.00-00           0x00000302   0xEE3B    819        0/0/0/3
  LEAF3.00-00           0x00000001   0x28E5    827        0/0/0/3
  SPINE1.00-00        * 0x00000013   0x1A1C    850        0/0/0/3
  SPINE2.00-00          0x00000014   0x7AB1    849        0/0/0/3
  SS.00-00              0x0000000F   0xC2AA    839        0/0/0/3

### Резултаты ping по всем узлам сети
SPINE1(config-if)# ping 10.10.10.10 count 2
PING 10.10.10.10 (10.10.10.10): 56 data bytes
64 bytes from 10.10.10.10: icmp_seq=0 ttl=254 time=42.783 ms
64 bytes from 10.10.10.10: icmp_seq=1 ttl=254 time=8.672 ms

--- 10.10.10.10 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 8.672/25.727/42.783 ms
SPINE1(config-if)# ping 10.1.0.1 count 2
PING 10.1.0.1 (10.1.0.1): 56 data bytes
64 bytes from 10.1.0.1: icmp_seq=0 ttl=255 time=4.912 ms
64 bytes from 10.1.0.1: icmp_seq=1 ttl=255 time=1.629 ms

--- 10.1.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 1.629/3.27/4.912 ms
SPINE1(config-if)# ping 10.2.0.1 count 2
PING 10.2.0.1 (10.2.0.1): 56 data bytes
64 bytes from 10.2.0.1: icmp_seq=0 ttl=253 time=65.124 ms
64 bytes from 10.2.0.1: icmp_seq=1 ttl=253 time=61.933 ms

--- 10.2.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 61.933/63.528/65.124 ms
SPINE1(config-if)# ping 10.0.1.1 count 2
PING 10.0.1.1 (10.0.1.1): 56 data bytes
64 bytes from 10.0.1.1: icmp_seq=0 ttl=254 time=17.809 ms
64 bytes from 10.0.1.1: icmp_seq=1 ttl=254 time=16.43 ms

--- 10.0.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 16.43/17.119/17.809 ms
SPINE1(config-if)# ping 10.0.2.1 count 2
PING 10.0.2.1 (10.0.2.1): 56 data bytes
64 bytes from 10.0.2.1: icmp_seq=0 ttl=254 time=51.736 ms
64 bytes from 10.0.2.1: icmp_seq=1 ttl=254 time=13.069 ms

--- 10.0.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 13.069/32.402/51.736 ms
SPINE1(config-if)# ping 10.0.3.1 count 2
PING 10.0.3.1 (10.0.3.1): 56 data bytes
64 bytes from 10.0.3.1: icmp_seq=0 ttl=254 time=16.333 ms
64 bytes from 10.0.3.1: icmp_seq=1 ttl=254 time=12.378 ms

--- 10.0.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 12.378/14.355/16.333 ms
SPINE1(config-if)# ping 172.16.1.1 count 2
PING 172.16.1.1 (172.16.1.1): 56 data bytes
64 bytes from 172.16.1.1: icmp_seq=0 ttl=62 time=22.473 ms
64 bytes from 172.16.1.1: icmp_seq=1 ttl=62 time=7.259 ms

--- 172.16.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 7.259/14.865/22.473 ms
SPINE1(config-if)# ping 172.16.2.1 count 2
PING 172.16.2.1 (172.16.2.1): 56 data bytes
64 bytes from 172.16.2.1: icmp_seq=0 ttl=62 time=22.303 ms
64 bytes from 172.16.2.1: icmp_seq=1 ttl=62 time=9.311 ms

--- 172.16.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 9.311/15.807/22.303 ms
SPINE1(config-if)# ping 172.16.3.1 count 2
PING 172.16.3.1 (172.16.3.1): 56 data bytes
64 bytes from 172.16.3.1: icmp_seq=0 ttl=62 time=65.779 ms
64 bytes from 172.16.3.1: icmp_seq=1 ttl=62 time=15.908 ms

--- 172.16.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 15.908/40.843/65.779 ms
SPINE1(config-if)# ping 172.16.4.1 count 2
PING 172.16.4.1 (172.16.4.1): 56 data bytes
64 bytes from 172.16.4.1: icmp_seq=0 ttl=62 time=36.736 ms
64 bytes from 172.16.4.1: icmp_seq=1 ttl=62 time=29.933 ms

--- 172.16.4.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 29.933/33.334/36.736 ms
SPINE1(config-if)#



## Spine2 
### ISIS Adjacency
SPINE2# sh isis adjacency
IS-IS process: Underlay VRF: default
IS-IS adjacency database:
Legend: '!': No AF level connectivity in given topology
System ID       SNPA            Level  State  Hold Time  Interface
LEAF2           N/A             1-2    UP     00:00:30   Ethernet1/1
LEAF1           N/A             1-2    UP     00:00:31   Ethernet1/2
SS              N/A             1-2    UP     00:00:29   Ethernet1/3
LEAF3           N/A             1-2    UP     00:00:21   Ethernet1/4


### ISIS Database и резултаты ping по всем узлам сети
SPINE2# sh isis database
IS-IS Process: Underlay LSP database VRF: default
IS-IS Level-1 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x00000012   0x082C    825        0/0/0/3
  LEAF2.00-00           0x00000302   0xEE3B    649        0/0/0/3
  LEAF3.00-00           0x00000001   0x28E5    666        0/0/0/3
  SPINE1.00-00          0x00000013   0x1A1C    687        0/0/0/3
  SPINE2.00-00        * 0x00000014   0x7AB1    690        0/0/0/3
  SS.00-00              0x0000000F   0xC2AA    939        0/0/0/3

IS-IS Level-2 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x00000012   0x082C    740        0/0/0/3
  LEAF2.00-00           0x00000302   0xEE3B    658        0/0/0/3
  LEAF3.00-00           0x00000001   0x28E5    666        0/0/0/3
  SPINE1.00-00          0x00000013   0x1A1C    688        0/0/0/3
  SPINE2.00-00        * 0x00000014   0x7AB1    690        0/0/0/3
  SS.00-00              0x0000000F   0xC2AA    678        0/0/0/3

### Резултаты ping по всем узлам сети
SPINE2# ping 10.10.10.10 count 2
PING 10.10.10.10 (10.10.10.10): 56 data bytes
64 bytes from 10.10.10.10: icmp_seq=0 ttl=254 time=40.033 ms
64 bytes from 10.10.10.10: icmp_seq=1 ttl=254 time=8.467 ms

--- 10.10.10.10 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 8.467/24.25/40.033 ms
SPINE2# ping 10.1.0.1 count 2
PING 10.1.0.1 (10.1.0.1): 56 data bytes
64 bytes from 10.1.0.1: icmp_seq=0 ttl=253 time=67.529 ms
64 bytes from 10.1.0.1: icmp_seq=1 ttl=253 time=47.554 ms

--- 10.1.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 47.554/57.541/67.529 ms
SPINE2# ping 10.2.0.1 count 2
PING 10.2.0.1 (10.2.0.1): 56 data bytes
64 bytes from 10.2.0.1: icmp_seq=0 ttl=255 time=2.285 ms
64 bytes from 10.2.0.1: icmp_seq=1 ttl=255 time=0.803 ms

--- 10.2.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 0.803/1.544/2.285 ms
SPINE2# ping 10.0.1.1 count 2
PING 10.0.1.1 (10.0.1.1): 56 data bytes
64 bytes from 10.0.1.1: icmp_seq=0 ttl=254 time=18.45 ms
64 bytes from 10.0.1.1: icmp_seq=1 ttl=254 time=7.113 ms

--- 10.0.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 7.113/12.781/18.45 ms
SPINE2# ping 10.0.2.1 count 2
PING 10.0.2.1 (10.0.2.1): 56 data bytes
64 bytes from 10.0.2.1: icmp_seq=0 ttl=254 time=38.836 ms
64 bytes from 10.0.2.1: icmp_seq=1 ttl=254 time=9.452 ms

--- 10.0.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 9.452/24.143/38.836 ms
SPINE2# ping 10.0.3.1 count 2
PING 10.0.3.1 (10.0.3.1): 56 data bytes
64 bytes from 10.0.3.1: icmp_seq=0 ttl=254 time=14.395 ms
64 bytes from 10.0.3.1: icmp_seq=1 ttl=254 time=6.365 ms

--- 10.0.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 6.365/10.379/14.395 ms
SPINE2# ping 172.16.1.1 count 2
PING 172.16.1.1 (172.16.1.1): 56 data bytes
64 bytes from 172.16.1.1: icmp_seq=0 ttl=62 time=55.514 ms
64 bytes from 172.16.1.1: icmp_seq=1 ttl=62 time=25.76 ms

--- 172.16.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 25.76/40.637/55.514 ms
SPINE2# ping 172.16.2.1 count 2
PING 172.16.2.1 (172.16.2.1): 56 data bytes
64 bytes from 172.16.2.1: icmp_seq=0 ttl=62 time=35.952 ms
64 bytes from 172.16.2.1: icmp_seq=1 ttl=62 time=10.165 ms

--- 172.16.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 10.165/23.058/35.952 ms
SPINE2# ping 172.16.3.1 count 2
PING 172.16.3.1 (172.16.3.1): 56 data bytes
64 bytes from 172.16.3.1: icmp_seq=0 ttl=62 time=26.047 ms
64 bytes from 172.16.3.1: icmp_seq=1 ttl=62 time=8.317 ms

--- 172.16.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 8.317/17.181/26.047 ms
SPINE2# ping 172.16.4.1 count 2
PING 172.16.4.1 (172.16.4.1): 56 data bytes
64 bytes from 172.16.4.1: icmp_seq=0 ttl=62 time=56.9 ms
64 bytes from 172.16.4.1: icmp_seq=1 ttl=62 time=13.614 ms

--- 172.16.4.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 13.614/35.256/56.9 ms


## Leaf1 
### ISIS Adjacency
LEAF1# sh isis adjacency
IS-IS process: Underlay VRF: default
IS-IS adjacency database:
Legend: '!': No AF level connectivity in given topology
System ID       SNPA            Level  State  Hold Time  Interface
SPINE1          N/A             1-2    UP     00:00:28   Ethernet1/1
SPINE2          N/A             1-2    UP     00:00:24   Ethernet1/2


### ISIS Database
LEAF1# sh isis database
IS-IS Process: Underlay LSP database VRF: default
IS-IS Level-1 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00         * 0x00000013   0x062D    863        0/0/0/3
  LEAF2.00-00           0x00000303   0xEC3C    690        0/0/0/3
  LEAF3.00-00           0x00000002   0x26E6    647        0/0/0/3
  SPINE1.00-00          0x00000014   0x181D    712        0/0/0/3
  SPINE2.00-00          0x00000016   0x76B3    1186       0/0/0/3
  SS.00-00              0x00000010   0xC0AB    938        0/0/0/3

IS-IS Level-2 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00         * 0x00000013   0x062D    738        0/0/0/3
  LEAF2.00-00           0x00000304   0xEA3D    1182       0/0/0/3
  LEAF3.00-00           0x00000002   0x26E6    703        0/0/0/3
  SPINE1.00-00          0x00000014   0x181D    732        0/0/0/3
  SPINE2.00-00          0x00000015   0x78B2    654        0/0/0/3
  SS.00-00              0x00000010   0xC0AB    668        0/0/0/3


### Резултаты ping по всем узлам сети
LEAF1# ping 10.10.10.10 count 2
PING 10.10.10.10 (10.10.10.10): 56 data bytes
64 bytes from 10.10.10.10: icmp_seq=0 ttl=253 time=96.418 ms
64 bytes from 10.10.10.10: icmp_seq=1 ttl=253 time=34.066 ms

--- 10.10.10.10 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 34.066/65.242/96.418 ms
LEAF1# ping 10.1.0.1 count 2
PING 10.1.0.1 (10.1.0.1): 56 data bytes
64 bytes from 10.1.0.1: icmp_seq=0 ttl=254 time=22.109 ms
64 bytes from 10.1.0.1: icmp_seq=1 ttl=254 time=10.461 ms

--- 10.1.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 10.461/16.285/22.109 ms
LEAF1# ping 10.2.0.1 count 2
PING 10.2.0.1 (10.2.0.1): 56 data bytes
64 bytes from 10.2.0.1: icmp_seq=0 ttl=254 time=17.929 ms
64 bytes from 10.2.0.1: icmp_seq=1 ttl=254 time=11.98 ms

--- 10.2.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 11.98/14.954/17.929 ms
LEAF1# ping 10.0.1.1 count 2
PING 10.0.1.1 (10.0.1.1): 56 data bytes
64 bytes from 10.0.1.1: icmp_seq=0 ttl=255 time=6.813 ms
64 bytes from 10.0.1.1: icmp_seq=1 ttl=255 time=0.636 ms

--- 10.0.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 0.636/3.724/6.813 ms
LEAF1# ping 10.0.2.1 count 2
PING 10.0.2.1 (10.0.2.1): 56 data bytes
64 bytes from 10.0.2.1: icmp_seq=0 ttl=253 time=89.259 ms
64 bytes from 10.0.2.1: icmp_seq=1 ttl=253 time=34.694 ms

--- 10.0.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 34.694/61.976/89.259 ms
LEAF1# ping 10.0.3.1 count 2
PING 10.0.3.1 (10.0.3.1): 56 data bytes
64 bytes from 10.0.3.1: icmp_seq=0 ttl=253 time=41.626 ms
64 bytes from 10.0.3.1: icmp_seq=1 ttl=253 time=13.212 ms

--- 10.0.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 13.212/27.419/41.626 ms
LEAF1# ping 172.16.1.1 count 2
PING 172.16.1.1 (172.16.1.1): 56 data bytes
64 bytes from 172.16.1.1: icmp_seq=0 ttl=63 time=10.735 ms
64 bytes from 172.16.1.1: icmp_seq=1 ttl=63 time=10.89 ms

--- 172.16.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 10.735/10.812/10.89 ms
LEAF1# ping 172.16.2.1 count 2
PING 172.16.2.1 (172.16.2.1): 56 data bytes
64 bytes from 172.16.2.1: icmp_seq=0 ttl=61 time=47.872 ms
64 bytes from 172.16.2.1: icmp_seq=1 ttl=61 time=64.921 ms

--- 172.16.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 47.872/56.396/64.921 ms
LEAF1# ping 172.16.3.1 count 2
PING 172.16.3.1 (172.16.3.1): 56 data bytes
64 bytes from 172.16.3.1: icmp_seq=0 ttl=61 time=69.597 ms
64 bytes from 172.16.3.1: icmp_seq=1 ttl=61 time=32.977 ms

--- 172.16.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 32.977/51.286/69.597 ms
LEAF1# ping 172.16.4.1 count 2
PING 172.16.4.1 (172.16.4.1): 56 data bytes
64 bytes from 172.16.4.1: icmp_seq=0 ttl=61 time=39.507 ms
64 bytes from 172.16.4.1: icmp_seq=1 ttl=61 time=54.497 ms

--- 172.16.4.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 39.507/47.002/54.497 ms


## Leaf2 
### ISIS Adjacency
LEAF2(config-if)# sh isis adjacency
IS-IS process: Underlay VRF: default
IS-IS adjacency database:
Legend: '!': No AF level connectivity in given topology
System ID       SNPA            Level  State  Hold Time  Interface
SPINE2          N/A             1-2    UP     00:00:26   Ethernet1/1
SPINE1          N/A             1-2    UP     00:00:26   Ethernet1/2


### ISIS Database
LEAF2(config-if)# sh isis database
IS-IS Process: Underlay LSP database VRF: default
IS-IS Level-1 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x00000013   0x062D    720        0/0/0/3
  LEAF2.00-00         * 0x00000304   0xEA3D    1137       0/0/0/3
  LEAF3.00-00           0x00000003   0x24E7    1061       0/0/0/3
  SPINE1.00-00          0x00000015   0x161E    1168       0/0/0/3
  SPINE2.00-00          0x00000016   0x76B3    1046       0/0/0/3
  SS.00-00              0x00000010   0xC0AB    798        0/0/0/3

IS-IS Level-2 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x00000014   0x042E    1108       0/0/0/3
  LEAF2.00-00         * 0x00000304   0xEA3D    1043       0/0/0/3
  LEAF3.00-00           0x00000003   0x24E7    1148       0/0/0/3
  SPINE1.00-00          0x00000015   0x161E    1188       0/0/0/3
  SPINE2.00-00          0x00000016   0x76B3    1093       0/0/0/3
  SS.00-00              0x00000011   0xBEAC    1076       0/0/0/3


### Резултаты ping по всем узлам сети

LEAF2(config-if)# ping 10.10.10.10 count 2
PING 10.10.10.10 (10.10.10.10): 56 data bytes
64 bytes from 10.10.10.10: icmp_seq=0 ttl=253 time=70.265 ms
64 bytes from 10.10.10.10: icmp_seq=1 ttl=253 time=28.525 ms

--- 10.10.10.10 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 28.525/49.395/70.265 ms
LEAF2(config-if)# ping 10.1.0.1 count 2
PING 10.1.0.1 (10.1.0.1): 56 data bytes
64 bytes from 10.1.0.1: icmp_seq=0 ttl=254 time=352.053 ms
64 bytes from 10.1.0.1: icmp_seq=1 ttl=254 time=225.008 ms

--- 10.1.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 225.008/288.53/352.053 ms
LEAF2(config-if)# ping 10.2.0.1 count 2
PING 10.2.0.1 (10.2.0.1): 56 data bytes
64 bytes from 10.2.0.1: icmp_seq=0 ttl=254 time=15.433 ms
64 bytes from 10.2.0.1: icmp_seq=1 ttl=254 time=12.122 ms

--- 10.2.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 12.122/13.777/15.433 ms
LEAF2(config-if)# ping 10.0.1.1 count 2
PING 10.0.1.1 (10.0.1.1): 56 data bytes
64 bytes from 10.0.1.1: icmp_seq=0 ttl=253 time=63.462 ms
64 bytes from 10.0.1.1: icmp_seq=1 ttl=253 time=37.091 ms

--- 10.0.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 37.091/50.276/63.462 ms
LEAF2(config-if)# ping 10.0.2.1 count 2
PING 10.0.2.1 (10.0.2.1): 56 data bytes
64 bytes from 10.0.2.1: icmp_seq=0 ttl=255 time=14.09 ms
64 bytes from 10.0.2.1: icmp_seq=1 ttl=255 time=3.473 ms

--- 10.0.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 3.473/8.781/14.09 ms
LEAF2(config-if)# ping 10.0.3.1 count 2
PING 10.0.3.1 (10.0.3.1): 56 data bytes
64 bytes from 10.0.3.1: icmp_seq=0 ttl=253 time=20.298 ms
64 bytes from 10.0.3.1: icmp_seq=1 ttl=253 time=26.152 ms

--- 10.0.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 20.298/23.224/26.152 ms
LEAF2(config-if)# ping 172.16.1.1 count 2
PING 172.16.1.1 (172.16.1.1): 56 data bytes
64 bytes from 172.16.1.1: icmp_seq=0 ttl=61 time=61.864 ms
64 bytes from 172.16.1.1: icmp_seq=1 ttl=61 time=37.34 ms

--- 172.16.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 37.34/49.601/61.864 ms
LEAF2(config-if)# ping 172.16.2.1 count 2
PING 172.16.2.1 (172.16.2.1): 56 data bytes
64 bytes from 172.16.2.1: icmp_seq=0 ttl=63 time=17.335 ms
64 bytes from 172.16.2.1: icmp_seq=1 ttl=63 time=9.219 ms

--- 172.16.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 9.219/13.277/17.335 ms
LEAF2(config-if)# ping 172.16.3.1 count 2
PING 172.16.3.1 (172.16.3.1): 56 data bytes
64 bytes from 172.16.3.1: icmp_seq=0 ttl=61 time=72.076 ms
64 bytes from 172.16.3.1: icmp_seq=1 ttl=61 time=18.202 ms

--- 172.16.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 18.202/45.138/72.076 ms
LEAF2(config-if)# ping 172.16.4.1 count 2
PING 172.16.4.1 (172.16.4.1): 56 data bytes
64 bytes from 172.16.4.1: icmp_seq=0 ttl=61 time=65.654 ms
64 bytes from 172.16.4.1: icmp_seq=1 ttl=61 time=39.768 ms

--- 172.16.4.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 39.768/52.71/65.654 ms
LEAF2(config-if)#
LEAF2(config-if)#

## Leaf3 
### ISIS Adjacency
LEAF3(config-router)# sh isis adjacency
IS-IS process: Underlay VRF: default
IS-IS adjacency database:
Legend: '!': No AF level connectivity in given topology
System ID       SNPA            Level  State  Hold Time  Interface
SPINE1          N/A             1-2    UP     00:00:30   Ethernet1/3
SPINE2          N/A             1-2    UP     00:00:21   Ethernet1/4


### ISIS Database
LEAF3(config-router)# sh isis database
IS-IS Process: Underlay LSP database VRF: default
IS-IS Level-1 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x00000014   0x042E    953        0/0/0/3
  LEAF2.00-00           0x00000304   0xEA3D    846        0/0/0/3
  LEAF3.00-00         * 0x00000003   0x24E7    773        0/0/0/3
  SPINE1.00-00          0x00000015   0x161E    878        0/0/0/3
  SPINE2.00-00          0x00000016   0x76B3    756        0/0/0/3
  SS.00-00              0x00000011   0xBEAC    1052       0/0/0/3

IS-IS Level-2 Link State Database
  LSPID                 Seq Number   Checksum  Lifetime   A/P/O/T
  LEAF1.00-00           0x00000014   0x042E    818        0/0/0/3
  LEAF2.00-00           0x00000304   0xEA3D    751        0/0/0/3
  LEAF3.00-00         * 0x00000003   0x24E7    860        0/0/0/3
  SPINE1.00-00          0x00000015   0x161E    898        0/0/0/3
  SPINE2.00-00          0x00000016   0x76B3    803        0/0/0/3
  SS.00-00              0x00000011   0xBEAC    786        0/0/0/3


### Резултаты ping по всем узлам сети
LEAF3(config-router)# ping 10.10.10.10 count 2
PING 10.10.10.10 (10.10.10.10): 56 data bytes
64 bytes from 10.10.10.10: icmp_seq=0 ttl=253 time=80.126 ms
64 bytes from 10.10.10.10: icmp_seq=1 ttl=253 time=31.686 ms

--- 10.10.10.10 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 31.686/55.906/80.126 ms
LEAF3(config-router)# ping 10.1.0.1 count 2
PING 10.1.0.1 (10.1.0.1): 56 data bytes
64 bytes from 10.1.0.1: icmp_seq=0 ttl=254 time=23.26 ms
64 bytes from 10.1.0.1: icmp_seq=1 ttl=254 time=6.187 ms

--- 10.1.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 6.187/14.723/23.26 ms
LEAF3(config-router)# ping 10.2.0.1 count 2
PING 10.2.0.1 (10.2.0.1): 56 data bytes
64 bytes from 10.2.0.1: icmp_seq=0 ttl=254 time=14.583 ms
64 bytes from 10.2.0.1: icmp_seq=1 ttl=254 time=6.764 ms

--- 10.2.0.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 6.764/10.673/14.583 ms
LEAF3(config-router)# ping 10.0.1.1 count 2
PING 10.0.1.1 (10.0.1.1): 56 data bytes
64 bytes from 10.0.1.1: icmp_seq=0 ttl=253 time=59.375 ms
64 bytes from 10.0.1.1: icmp_seq=1 ttl=253 time=53.513 ms

--- 10.0.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 53.513/56.444/59.375 ms
LEAF3(config-router)# ping 10.0.2.1 count 2
PING 10.0.2.1 (10.0.2.1): 56 data bytes
64 bytes from 10.0.2.1: icmp_seq=0 ttl=253 time=70.813 ms
64 bytes from 10.0.2.1: icmp_seq=1 ttl=253 time=28.778 ms

--- 10.0.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 28.778/49.795/70.813 ms
LEAF3(config-router)# ping 10.0.3.1 count 2
PING 10.0.3.1 (10.0.3.1): 56 data bytes
64 bytes from 10.0.3.1: icmp_seq=0 ttl=255 time=3.558 ms
64 bytes from 10.0.3.1: icmp_seq=1 ttl=255 time=1.222 ms

--- 10.0.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 1.222/2.39/3.558 ms
LEAF3(config-router)# ping 172.16.1.1 count 2
PING 172.16.1.1 (172.16.1.1): 56 data bytes
64 bytes from 172.16.1.1: icmp_seq=0 ttl=61 time=53.233 ms
64 bytes from 172.16.1.1: icmp_seq=1 ttl=61 time=87.447 ms

--- 172.16.1.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 53.233/70.34/87.447 ms
LEAF3(config-router)# ping 172.16.2.1 count 2
PING 172.16.2.1 (172.16.2.1): 56 data bytes
64 bytes from 172.16.2.1: icmp_seq=0 ttl=61 time=52.095 ms
64 bytes from 172.16.2.1: icmp_seq=1 ttl=61 time=15.549 ms

--- 172.16.2.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 15.549/33.822/52.095 ms
LEAF3(config-router)# ping 172.16.3.1 count 2
PING 172.16.3.1 (172.16.3.1): 56 data bytes
64 bytes from 172.16.3.1: icmp_seq=0 ttl=63 time=8.239 ms
64 bytes from 172.16.3.1: icmp_seq=1 ttl=63 time=2.607 ms

--- 172.16.3.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 2.607/5.423/8.239 ms
LEAF3(config-router)# ping 172.16.4.1 count 2
PING 172.16.4.1 (172.16.4.1): 56 data bytes
64 bytes from 172.16.4.1: icmp_seq=0 ttl=63 time=9.807 ms
64 bytes from 172.16.4.1: icmp_seq=1 ttl=63 time=10.819 ms

--- 172.16.4.1 ping statistics ---
2 packets transmitted, 2 packets received, 0.00% packet loss
round-trip min/avg/max = 9.807/10.313/10.819 ms

