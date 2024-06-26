# Задача о рюкзаке (Knapsack problem)
Для каждого варианта представлены условия задачи, в соответствии с которыми необходимо: 
1. Решить задачу о рюкзаке с применением метода ветвей и границ.
2. Оформить решение задачи по шагам с подробными комментариями, таблицами и диаграммами.
3. В ответе указать:
   - максимально возможную стоимость предметов в рюкзаке,
   - набор предметов, обеспечивающих максимальную стоимость,
   - общий вес предметов в рюкзаке,
   - свободное место в рюкзаке.

## Условие задачи

### Вариант 7:

| Предметы  | A | B  | C  | D | E  |
|:----------|:-:|:--:|:--:|:-:|:--:|
| Стоимость | 9 | 5  | 18 | 8 | 3  |
| Вес       | 9 | 10 | 6  | 4 | 12 |

Ограничение вместимости: 15

# Решение

## Шаг I - Найдём ценность каждого предмета, для этого необходимо разделить стоимость каждого предмета на его вес

### Получаем следующую таблицу с ценностями:

| Предметы  | A |  B  | C  | D |  E  |
|:----------|:-:|:---:|:--:|:-:|:---:|
| Стоимость | 9 |  5  | 18 | 8 |  3  |
| Вес       | 9 | 10  | 6  | 4 | 12  |
| Ценность  | 1 | 1/2 | 3  | 2 | 1/4 |

## Шаг II - Отсортируем таблицу по убыванию ценности

### Получаем изменённую таблицу

| Предметы  | C  | D | A |  B  |  E  |
|:----------|:--:|:-:|:-:|:---:|:---:|
| Стоимость | 18 | 8 | 9 |  5  |  3  |
| Вес       | 6  | 4 | 9 | 10  | 12  |
| Ценность  | 3  | 2 | 1 | 1/2 | 1/4 |

## Шаг III - Рассчитаем оценку сверху для пустого рюкзака

### Для этого необходимо свободное место в рюкзаке (15) умножить на наибольшую ценность предмета (3), тогда получим, что оценка сверху: 15*3 = 45

## Шаг IV - Решим задачу с помощью метода ветвей и границ

### Тогда получим следующее дерево

```mermaid
graph TB
    1(#1\n15*3=45)-->|-С|2(#2\n15*2=30)
    1-->|+C|3(#3\n18+9*2=36)
    3-->|-D|4(#4\n18+9*1=27)
    3-->|+D|5(#5\n18+8+5*1=31)
    5-->|-A|6(#6\n18+8+5*0.5=28.5)
    5-->|+A|7(#7\n0)
    2-->|-D|8(#8\n15*1=15)
    2-->|+D|9(#9\n8+11*1=19)
    6-->|-B|10(#10\n18+8+5*0.25=27.25)
    6-->|+B|11(#11\n0)
    10-->|-E|12(#12\n18+8+5*0=26)
    10-->|+E|13(#13\n0)
    4-->|-A|14(#14\n18+9*0.5=22.5)
    4-->|+A|15(#15\n18+9+0*0.5=27)
    15-->|-B|16(#16\n18+9+0*0.25=27)
    15-->|+B|17(#17\n0)
    16-->|-E|18(#18\n18+9+0*0=27)
    16-->|+E|19(#19\n0)
```

### Ответ
- Наибольшая стоимость предметов в рюкзаке 27.
- Набор предметов, обеспечивающих максимальную стоимость, C, A, общим весом 15.
- Свободное место в рюкзаке 0.
