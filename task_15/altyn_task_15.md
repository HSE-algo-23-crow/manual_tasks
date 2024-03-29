﻿## Постановка задачи
1. Дана сеть (взвешенный ориентированный граф) с источником s и стоком t.
2. Для каждой дуги определена пропускная способность и стоимость транспортировки.
3. Необходимо найти для указанной сети максимальный поток минимальной стоимости. 

## Решение задачи на поиск в сети максимального потока минимальной стоимости

Пропускная способность дуг сети и стоимость транспортировки указана в таблице.

### Вариант 6:
| Дуги                      | sa | sc | ab | ad | ac | cd | bd | dt |
|:--------------------------|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Пропускная способность    | 9  | 9  | 5  | 5  | 5  | 11 | 5  | 11 |
| Стоимость транспортировки | 3  | 3  | 3  | 6  | 3  | 8  | 3  | 3  |
### 1. Построим сеть с источником **s**, стоком **t** и указанными пропускными способностями дуг для поиска максимального потока.

```mermaid
graph LR
    s-->|9|a
    s-->|4|b
    s-->|9|c
    a-->|5|c
    a-->|5|b
    a-->|5|d
    b-->|5|d
    c-->|11|d
    d-->|11|t
```
Укажем начальный поток величиной 9 **s -> c -> d -> t**. Построим соответствующую остаточную сеть.
```mermaid
graph LR
    a-.->|9|s
    s-->|4|b
    s-->|9|c
    c-.->|5|a
    b-.->|5|a
    d-.->|5|a
    d-.->|5|b
    c-->|9|d
    d-->|2|c
    d-->|9|t
    t-->|2|d
```
### 2. Проведем поиск увеличивающего пути в остаточной сети
В остаточной сети найден увеличивающий путь t -> d -> a -> s. Минимальный вес дуг на этом пути равен 2.

Уменьшим вес дуг на найденном пути, дуги для которых вес стал нулевым удалим из остаточной сети. 
```mermaid
graph LR
    a-.->|7|s
    s-->|2|a
    s-->|9|c
    c-.->|5|a
    b-.->|5|a
    d-.->|3|a
    a-->|2|d
    d-.->|5|b
    c-->|9|d
    d-.->|2|c
    d-->|11|t
```
В остаточной сети не найдено увеличивающих путей, следовательно, алгоритм завершил работу и найденный поток величиной 11 является максимальным для данной сети. 
```mermaid
graph LR

    s-->|2,9|a
    s-->|9,9|c
    a-->|0,5|c
    a-->|0,5|b
    a-->|2,5|d
    b-->|0,5|d
    c-->|9,11|d
    d-->|11,11|t
```
### 3. Попробуем уменьшить стоимость потока для чего построим остаточную сеть.
Для каждого ребра остаточной сети укажем стоимость транспортировки единицы потока.
```mermaid
graph LR
    a-.->|+3|s
    s-->|-3|a
    s-->|-3|c
    c-.->|+3|a
    b-.->|+3|a
    d-.->|+6|a
    a-->|-6|d
    d-.->|+3|b
    c-->|-8|d
    d-.->|+8|c
    d-->|-3|t
```
В остаточной сети найден ориентированный цикл отрицательной стоимости s -> c -> d -> b -> a -> s (- 3 - 8 + 3 + 3 + 3 = -2). 
Найдем минимальный вес ребра в указанном цикле, изображенном **в остаточной сети с указанием величины потока**. 
```mermaid
graph LR
    a-.->|7|s
    s-->|2|a
    s-->|9|c
    c-.->|5|a
    b-.->|5|a
    d-.->|3|a
    a-->|2|d
    d-.->|5|b
    c-->|9|d
    d-.->|2|c
    d-->|11|t
```
Минимальный вес ребра в цикле 5 - это неиспользованный резерв ребра d -> b.

Удалим найденный цикл - уменьшим на 5 вес всех ребер, входящих в цикл.
```mermaid
graph LR
    a-.->|2|s
    s-->|7|a
    s-->|4|c
    c-.->|5|s
    c-.->|5|a
    a-->|5|b
    d-.->|3|a
    a-->|2|d
    b-->|5|d
    c-->|4|d
    d-.->|7|c
    d-->|11|t
```
### 4. Проведем повторный поиск цикла отрицательной стоимости в остаточной сети.
Скорректируем остаточную сеть с указанием стоимости транспортировки единицы потока.
```mermaid
graph LR
    a-.->|+3|s
    s-->|-3|a
    s-->|-3|c
    c-.->|+3|s
    c-.->|+3|a
    a-->|-3|b
    d-.->|+6|a
    a-->|-6|d
    b-->|-3|d
    c-->|-8|d
    d-.->|+8|c
    d-->|-3|t
```
В остаточной сети найден ориентированный цикл отрицательной стоимости s -> c -> d -> a -> s (- 3 - 8 + 6 + 3 = -2). 

Найдем минимальный вес ребра в указанном цикле, изображенном **в остаточной сети с указанием величины потока**.  
```mermaid
graph LR
    a-.->|2|s
    s-->|7|a
    s-->|4|c
    c-.->|5|s
    c-.->|5|a
    a-->|5|b
    d-.->|3|a
    a-->|2|d
    b-->|5|d
    c-->|4|d
    d-.->|7|c
    d-->|11|t
```
Минимальный вес ребра в цикле 2 - это неиспользованный резерв ребер s -> a

Удалим найденный цикл - уменьшим на 2 вес всех ребер, входящих в цикл.
```mermaid
graph LR
    a-.->|2|s
    s-->|7|a
    s-->|2|c
    c-.->|7|s
    c-.->|5|a
    a-->|5|b
    d-.->|1|a
    a-->|4|d
    b-->|5|d
    c-->|2|d
    d-.->|9|c
    d-->|11|t
```
### 5. Проведем повторный поиск цикла отрицательной стоимости в остаточной сети.
Скорректируем остаточную сеть с указанием стоимости транспортировки единицы потока.
```mermaid
graph LR
    s-->|-3|a
    s-->|-3|c
    c-.->|+3|s
    c-.->|+3|a
    a-->|-3|b
    d-.->|+6|a
    a-->|-6|d
    b-->|-3|d
    c-->|-8|d
    d-.->|+8|c
    d-->|-3|t
```
В остаточной сети отсутствуют циклы отрицательной стоимости, следовательно, стоимость потока минимальна.
### 6. Рассчитаем стоимость полученного максимального потока.
| Дуги                      | sa | sc | ab | ad | ac | cd | bd | dt | Итого |
|:--------------------------|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Пропускная способность    | 9  | 9  | 5  | 5  | 5  | 11 | 5  | 11 | |
| Локальный поток f(e)                          | 9  | 2  | 5  | 4  | 0  | 2  | 5 | 11 | |
| Стоимость транспортировки | 3  | 3  | 3  | 6  | 3  | 8  | 3  | 3  | |
| Суммарная стоимость f(e)*c(e)                 | 27 | 6  | 15  | 24  | 0 | 16 | 15 | 33 | **136** |
Стоимость полученного потока составляет 136.
### Ответ:

Максимальный поток в сети равен 11, минимальная стоимость потока 136, она реализуется следующим локальными потоками:
```mermaid
graph LR
    s-->|9,9|a
    s-->|2,9|c
    a-->|0,5|c
    a-->|5,5|b
    a-->|4,5|d
    b-->|5,5|d
    c-->|2,11|d
    d-->|11,11|t
```
