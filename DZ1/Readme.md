Домашнее задание
Проектирование адресного пространства

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
          10.0.__Leaf__.1/32  

Проблемы связанные с расширением - если будет добавлен новый ЦОД, то нумерация новых Spine и Leaf может начинаться с 50 или 100, 
в зависимости от кол-ва узлов в первом ЦОДе.  

Схема адресного пространства
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ1/DZ-1-map%20of%20net1.JPG  "Схема адресного пространства")  

Таблица коммутации  
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ1/DZ-1-com%20table1.JPG)

