

Домашнее задание
Проектирование адресного пространства и построение сети ЦОД на OSPF

Допущения и предположения
1. используем LoopBack для построения сетевой связанности
2. Используем OSPF IP Unnumbered
3. Колличество клиентов - 4. На каждом используется по одной сети /24
4. Loopbak подняты на каждом узле Spine и Leaf с маской /32
5. Формат адреса Loopback  
          10.__Spine__.0.1/32  
          10.0.__Leaf__.1/3
6. Добавлен уровень SuperSpine, состоящий из одного узла.
7. SuperSpine имеет Lo0 - 10.10.10.10/32
8. Настроен BFD на интерфейсах
9. Router-Id не настроен в ручную

Схема адресного пространства
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/dz2-shema%20seti-2UN1.JPG)  

## SuperSpine 
###Ospf Neighbor и Таблица маршутизации

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/SS/SuperSpine-Ospf-Nei-Route.PNG)

###Ospf database

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/SS/SuperSpine-Ospf-base.PNG)

###Проверка доступности всех роутеров

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/SS/SuperSpine-Ospf-base.PNG)

###Проверка доступности всех клиентов

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/SS/SuperSpine-Ospf-base.PNG)
