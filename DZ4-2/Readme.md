

Домашнее задание
Настроите eBGP в Underlay сети, для IP связанности между всеми сетевыми устройствами.

1. Кол-во клиентов в дальнейшем неизвестно.
2. Нумерация Spine начинается с 1
3. Нумерация Leaf начинается с 1
4. Нумерация Client начинается с 1
5. Линки между Spine и Leaf - маска /30
6. Линки между Leaf и Client  - маска /24
7. Loopbak подняты на каждом узле SS, Spine и Leaf с маской /32

__LoopBack не используем для построения связностей. Не используем unnumbered hosts.__

Схема адресного пространства
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ4-2/Shema-seti-new.JPG  "Схема адресного пространства")  

Таблица коммутации  
![alt-текст](https://github.com/AndreyIvanov1972/Otus-COD/blob/main/DZ4-2/new-table-comm.JPG)

