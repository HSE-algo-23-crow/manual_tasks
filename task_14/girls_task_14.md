## Задача о максимальном потоке
### Вариант 2:
|          Дуги          | sa | sс | aс | ba | cb | bt | at |
|:----------------------:|:--:|:--:|:--:|:--:|:--:|:--:|:--:|
| Пропускная способность | 9  | 7  | 8  | 5  | 11 | 10 | 3  |

1. **Построим сеть с источником s, стоком t и укажем пропускные способности:**

```mermaid
graph LR
    s -->|9|a
    s --> |7|c
    a --> |8|c
    c --> |11|b
    b --> |5|a
    b --> |10|t
    a --> |3|t
```
Построим остаточную сеть:

```mermaid
graph RL
    a -.-> |9|s
    c -.-> |7|s
    c -.-> |8|a
    a -.-> |5|b
    b -.-> |11|c
    t -.-> |10|b
    t -.-> |3|a
```

2. **Проведем поиск увеличивающего пути в остаточной сети:**

В остаточной сети есть увеличивающий путь t –> a –> s. Минимальный вес дуг, образующих этот путь, равен 3. Согласно алгоритму, уменьшаем веса дуг (t, a) и (a, s) в остаточной сети на 3. 
```mermaid
graph RL
    a --> |9|s
    c -.-> |7|s
    c -.-> |8|a
    a -.-> |5|b
    b -.-> |11|c
    t -.-> |10|b
    t --> |3|a
```
Скорректированный поток:
```mermaid
graph LR
    s-->|"(7)"|c
    s-->|"(3, 9)"|a
    a-->|"(8)"|c
    c-->|"(11)"|b
    b-->|"(5)"|a
    b-->|"(10)"|t
    a-->|"(3, 3)"|t
```
Скорректированная остаточная сеть:
```mermaid
graph RL
    s -->|3|a
    a -->|6|s
    c --> |7|s
    c --> |8|a
    b --> |11|c
    a --> |5|b
    t --> |10|b
    a --> |3|t
```
3. **Продолжим поиск увеличивающего пути в остаточной сети:**

В скорректированной остаточной сети есть увеличивающий путь t –> b –> c –> s с минимальным весом входящих в него ребер, равным 7.
```mermaid
graph RL
    a -.-> |9|s
    c --> |7|s
    c -.-> |8|a
    a -.-> |5|b
    b --> |11|c
    t --> |10|b
    t -.-> |3|a
```

Уменьшаем в остаточной сети веса дуг (t, b), (b, c) и (c, s) на 7 и одновременно с этим наращиваем поток в исходной сети с 3 до 10.

Увеличенный поток и соответствующая ему остаточная сеть: 
```mermaid
graph LR
    s-->|"(7,7)"|c
    s-->|"(3, 9)"|a
    a-->|"(8)"|c
    c-->|"(7,11)"|b
    b-->|"(5)"|a
    b-->|"(7,10)"|t
    a-->|"(3, 3)"|t
```
```mermaid
graph RL
    s -->|3|a
    a -->|6|s
    s -->|7|c
    c --> |8|a
    c -->|7|b
    b --> |4|c
    a --> |5|b
    t --> |3|b
    b --> |7|t
    a --> |3|t
```

4. **Продолжим поиск увеличивающего пути в остаточной сети:**

В скорректированной остаточной сети есть увеличивающий путь t –> b –> c –> a -> s с минимальным весом входящих в него ребер, равным 3.
```mermaid
graph RL
    a -.-> |9|s
    c --> |7|s
    c -.-> |8|a
    a --> |5|b
    b -.-> |11|c
    t -.-> |10|b
    t --> |3|a
```

Уменьшаем в остаточной сети веса дуг (t, b), (b, c), (c, a) и (a, s) на 3 и одновременно с этим наращиваем поток в исходной сети с 10 до 13.

Увеличенный поток и соответствующая ему остаточная сеть:
```mermaid
graph LR
    s-->|"(7,7)"|c
    s-->|"(6, 9)"|a
    a-->|"(3,8)"|c
    c-->|"(10,11)"|b
    b-->|"(5)"|a
    b-->|"(10,10)"|t
    a-->|"(3, 3)"|t
```
Из остаточной сети удаляем дугу (t, b), поскольку ее вес стал равен нулю:
```mermaid
graph RL
    s --> |6|a
    a --> |3|s
    s --> |7|c
    c --> |5|a
    a --> |3|c
    c --> |10|b
    b --> |5|c
    a --> |5|b
    b --> |10|t
    a --> |3|t
```
5. **Проверим значение максимального потока перебором всех разрезов сети**
Разрез сети - разбиение множества вершин на два подмножества V<sub>1</sub> и V<sub>2</sub>, где во множество V<sub>1</sub> входит источник, а в V<sub>2</sub> входит сток.

Пропускная способность разреза - сумма пропускной способности дуг, начинающихся в вершинах из множества V<sub>1</sub> и оканчивающихся в вершинах из V<sub>2</sub>.

Для сети из _n_ вершин существует 2<sup>n - 2</sup> различных разрезов, так как две вершины из множества (источник и сток) "зафиксированы" в V<sub>1</sub> и V<sub>2</sub>, остальные вершины можно различными способами распределять между множествами V<sub>1</sub> и V<sub>2</sub>.

Для сети из 5 вершин нужно найти 2<sup>5 - 2</sup> = 2<sup>3</sup> = 8 разрезов. 

| № | V<sub>1</sub>                   | V<sub>2</sub> | Пропускная способность разреза |
|---|:--------------------------------|:--------------|:------------------------------:|
| 1 | s                               | a, b, c, t    |           9 + 7 = 16           |
|   | **s + одна вершина из a, b, c** |               |                                |
| 2 | s, a                            | b, c, t       |    7  + 8 + 3  = 18            |
| 3 | s, b                            | a, c, t       |      9 + 7 + 5 + 10 = 31       |
| 4 | s, c                            | a, b, t       |          9 + 11 = 20           |
|   | **s + пара вершин из a, b, c**  |               |                                |
| 5 | s, a, b                         | c, t          |      7 + 8 + 3 + 10 = 28       |
| 6 | s, a, c                         | b, t          |          3 + 11  = 14          |
| 7 | s, b, c                         | a, t          |        9 + 5 + 10 = 24         |
|   | **s + три вершины из a, b, c**  |               |                                |
| 8 | s, a, b, c                      | t             |          3 + 10 = 13           |

Минимальная пропускная способность разреза равна 13 ( {s, a, b, c} / {t} ), что совпадает с найденной величиной максимального потока в сети.
**Алгоритм завершил свою работу, поскольку в остаточной сети больше нет увеличивающих путей. Найденный поток величины 13 является максимальным.**
