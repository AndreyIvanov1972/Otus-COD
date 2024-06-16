

Домашнее задание
Настроите eBGP в Underlay сети, для IP связанности между всеми сетевыми устройствами.

2. Кол-во клиентов в дальнейшем неизвестно.
3. Нумерация Spine начинается с 1
4. Нумерация Leaf начинается с 1
5. Нумерация Client начинается с 1
6. Линки между Spine и Leaf - маска /30
7. Линки между Leaf и Client  - маска /24
10. Loopbak подняты на каждом узле Spine и Leaf с маской /32
11. Формат адреса Loopback  
          10.__Spine__.0.1/32  
          10.0.__Leaf__.1/3

__LoopBack не используем для построения связностей. Не используем unnumbered hosts.__

Схема адресного пространства
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2/dz2-shema%20seti-1.JPG  "Схема адресного пространства")  

Таблица коммутации  
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2/HostConnectionTable.JPG)

