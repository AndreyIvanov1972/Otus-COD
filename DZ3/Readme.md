
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
### ISIS Adjacency, Database и резултаты ping по всем узлам сети

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/edit/main/DZ3/SS-result.txt)

### Ospf database

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/SS/SuperSpine-Ospf-base.PNG)

### Проверка доступности всех роутеров

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/SS/SS-ping-router.PNG)

### Проверка доступности всех клиентов

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/SS/SS-ping-client.PNG)

## Spine1 
### Ospf Neighbor и Таблица маршутизации

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Spine1/Spine1-Ospf-Nei-Route.PNG)

### Ospf database

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Spine1/Spine1-Ospf-base.PNG)

### Проверка доступности всех роутеров

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Spine1/Spine1-ping-router.PNG)

### Проверка доступности всех клиентов

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Spine1/Spine1-ping-client.PNG)

## Spine2 
### Ospf Neighbor и Таблица маршутизации

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Spine2/Spine2-Ospf-Nei-Route.PNG)

### Ospf database

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Spine2/Spine2-Ospf-base.PNG)

### Проверка доступности всех роутеров

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Spine2/Spine2-ping-router.PNG)

### Проверка доступности всех клиентов

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Spine2/Spine2-ping-client.PNG)

## Leaf1 
### Ospf Neighbor и Таблица маршутизации

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf1/Leaf1-Ospf-Nei-Route.PNG)

### Ospf database

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf1/Leaf1-Ospf-base.PNG)

### Проверка доступности всех роутеров

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf1/Leaf1-ping-router.PNG)

### Проверка доступности всех клиентов

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf1/Leaf1-ping-client.PNG)

## Leaf2 
### Ospf Neighbor и Таблица маршутизации

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf2/Leaf2-Ospf-Nei-Route.PNG)

### Ospf database

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf2/Leaf2-Ospf-base.PNG)

### Проверка доступности всех роутеров

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf2/Leaf2-ping-router.PNG)

### Проверка доступности всех клиентов

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf2/Leaf2-ping-client.PNG)

## Leaf3 
### Ospf Neighbor и Таблица маршутизации

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf3/Leaf3-Ospf-Nei-Route.PNG)

### Ospf database

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf3/Leaf3-Ospf-base.PNG)

### Проверка доступности всех роутеров

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf3/Leaf3-ping-router.PNG)

### Проверка доступности всех клиентов

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Leaf3/Leaf3-ping-client.PNG)

## Клиенты
### Клиент1 

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Clients/client1-ping%20route.PNG)

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Clients/client1-ping%20client.PNG)

### Клиент2

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Clients/client2-ping%20route.PNG)

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Clients/client2-ping%20client.PNG)

### Клиент3 

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Clients/client3-ping%20route.PNG)

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Clients/client3-ping%20client.PNG)

### Клиент4 

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Clients/client4-ping%20route.PNG)

![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ2-UNN/Clients/client4-ping%20client.PNG)



