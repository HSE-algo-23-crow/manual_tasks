# Задание №19
# Задача о рюкзаке (Knapsack problem)

## Задание
Для каждого варианта представлены условия задачи, в соответствии с которыми необходимо: 
1. Решить задачу о рюкзаке с применением метода ветвей и границ.
2. Оформить решение задачи по шагам с подробными комментариями, таблицами и диаграммами.
3. В ответе указать:
   - максимально возможную стоимость предметов в рюкзаке,
   - набор предметов, обеспечивающих максимальную стоимость,
   - общий вес предметов в рюкзаке,
   - свободное место в рюкзаке.

## Постановка задачи
Задача о рюкзаке (англ. Knapsack problem) — дано N предметов, n<sub>i</sub> предмет имеет массу w<sub>i</sub> > 0 и стоимость p<sub>i</sub> > 0. Необходимо выбрать из этих предметов такой набор, чтобы суммарная масса не превосходила заданной величины W (вместимость рюкзака), а суммарная стоимость была максимальна. 

## Пример решения задачи о рюкзаке
## Условия задачи - вариант 6
| Предметы  | A | B  | C  | D | E  |
|:----------|:-:|:--:|:--:|:-:|:--:|
| Стоимость | 8 | 3  | 18 | 8 | 5  |
| Вес       | 2 | 12 | 6  | 4 | 10 |

Ограничение вместимости: 16

## Решение
### 1. Рассчитаем ценность каждого предмета
| Предметы  | A |  B  | C  | D |  E  |
|:----------|:-:|:---:|:--:|:-:|:---:|
| Стоимость | 8 |  3  | 18 | 8 |  5  |
| Вес       | 2 | 12  | 6  | 4 | 10  |
| Ценность  | 4 | 1/4 | 3  | 2 | 1/2 |

### 2. Отсортируем предметы по убыванию ценности
| Предметы  | A | C  | D |  E  |  B  |
|:----------|:-:|:--:|:-:|:---:|:---:|
| Стоимость | 8 | 18 | 8 |  5  |  3  |
| Вес       | 2 | 6  | 4 | 10  | 12  |
| Ценность  | 4 | 3  | 2 | 1/2 | 1/4 |


### 3. Рассчитаем оценку сверху для пустого рюкзака

Свободное место в рюкзаке: 16

Наибольшая ценность предмета: 4

Оценка сверху для пустого рюкзака: 16 * 4 = 64


### 4. Найдем решение задачи с использованием метода ветвей и границ

```mermaid
graph TB
    1(#1\n16*4=64)-->|-A|2(#2\n16*3=48)
    1-->|+A|3(#3\n8+14*3=50)
    3-->|-C|4(#4\n8+14*2=36)
    3-->|+C|5(#5\n18+8+8*2=42)
    5-->|+D|9(#9\n18+8+8+4*0.5=36)
    9-->|-E|12(#12\n18+8+8+4*0.25=35)
    12-->|-B|14(#16\n18+8+8+4*0=34)
    12-->|+B|15(#17\n0)
    9-->|+E|13(#13\n0)
    5-->|-D|8(#8\n18+8+8*0.5=30)
    2-->|-C|6(#6\n16*2=32)
    2-->|+C|7(#7\n18+10*2=38)
    7-->|-D|16(#10\n18+10*0.5=23)
    7-->|+D|17(#11\n18+8+6*0.5=29)
    4-->|-D|10(#14\n8+14*0.5=15)
    4-->|+D|11(#15\n8+8+10*0.5=21)

```

### Ответ
- Наибольшая стоимость предметов в рюкзаке 34.
- Набор предметов, обеспечивающих максимальную стоимость, A, C, D, общим весом 12.
- Свободное место в рюкзаке 4.

