### Условия задачи для Mysterious:
| $   | A   | B   | C   | D   | E   |
|-----|-----|-----|-----|-----|-----|
| 100 | 3   | 5   | 4   | 7   | 1   |
| 200 | 7   | 10  | 8   | 9   | 8   |
| 300 | 9   | 12  | 14  | 10  | 9   |
| 400 | 13  | 15  | 16  | 14  | 11  |
| 500 | 16  | 18  | 19  | 15  | 15  |

## Решение 
### I этап. Фиксируем 2 проекта A, B и определяем наилучший вариант распределения между двумя проектами.
**100 $**: max(100A, 100B) = max(3, 5) = ***100B = 5***

**200 $**: max(100A+100B, 200A, 200B) = max(8, 7, 10) = ***200B = 10***

**300 $**: max(100A+200B, 200A+100B, 300A, 300B) = max(13, 12, 9, 12) = ***100A+200B = 13***

**400 $**: max(400A, 400B, 200A+200B, 100A+300B, 300A+100B) = max(13, 15, 17, 15, 14) = ***200A+200B = 17***

**500 $**: max(500A, 500B, 100A+400B, 400A+100B, 200A+300B, 300A+200B) = max(16, 18, 18, 18, 19, 19) = ***200A+300B = 19***

### II этап. Фиксируем AB и C.
| $   | A+B | C   | 
|-----|-----|-----|
| 100 | 5   | 4   | 
| 200 | 10  | 8   | 
| 300 | 13  | 14  | 
| 400 | 17  | 16  | 
| 500 | 19  | 19  |

**100 $**: max(100AB, 100C) = max(5, 4) = ***100AB = 5***

**200 $**: max(200AB, 200C, 100AB+100C) = max(10, 8, 9) = ***200AB = 10***

**300 $**: max(300AB, 300C, 100AB+200C, 200AB+100C) = max(13, 14, 13, 14) = ***300C = 14***

**400 $**: max(400AB, 400C, 100AB+300C, 300AB+100C, 200AB+200C) = max(17, 16, 19, 17, 18) = ***100AB+300C = 19***

**500 $**: max(500AB, 500C, 100AB+400C, 400AB+100C, 200AB+300C, 300AB+200C) = max(19, 19, 21, 21, 24, 21) = ***200AB+300C = 24***

### III этап. Фиксируем ABC и D.
| $   | A+B+C | D  | 
|-----|-------|----|
| 100 | 5     | 7  | 
| 200 | 10    | 9  | 
| 300 | 14    | 10 | 
| 400 | 19    | 14 | 
| 500 | 24    | 15 |

**100 $**: max(100ABC, 100D) = max(5, 7) = ***100D = 7***

**200 $**: max(200ABC, 200D, 100ABC+100D) = max(10, 9, 12) = ***100ABC+100D = 12***

**300 $**: max(300ABC, 300D, 100ABC+200D, 200ABC+100D) = max(14, 10, 14, 17) = ***200ABC+100D = 17***

**400 $**: max(400ABC, 400D, 100ABC+300D, 300ABC+100D, 200ABC+200D) = max(19, 14, 15, 21, 19) = ***300ABC+100D = 21***

**500 $**: max(500ABC, 500D, 100ABC+400D, 400ABC+100D, 200ABC+300D, 300ABC+200D) = max(24, 15, 19, 26, 20, 23) = ***400ABC+100D = 26***

### IV этап. Фиксируем ABCD и E.
| $   | A+B+C+D | E  | 
|-----|---------|----|
| 100 | 7       | 1  | 
| 200 | 12      | 8  | 
| 300 | 17      | 9  | 
| 400 | 21      | 11 | 
| 500 | 26      | 15 |

**100 $**: max(100ABCD, 100E) = max(7, 1) = ***100ABCD = 7***

**200 $**: max(200ABCD, 200E, 100ABCD+100E) = max(12, 8, 8) = ***200ABCD = 12***

**300 $**: max(300ABCD, 300E, 100ABCD+200E, 200ABCD+100e) = max(17, 9, 15, 13) = ***300ABCD = 17***

**400 $**: max(400ABCD, 400E, 100ABCD+300E, 300ABCD+100E, 200ABCD+200E) = max(21, 11, 16, 18, 20) = ***400ABCD = 21***

**500 $**: max(500ABCD, 500E, 100ABCD+400E, 400ABCD+100E, 200ABCD+300E, 300ABCD+200E) = max(26, 15, 18, 22, 21, 25) = ***500ABCD = 26***

### Итоговый результат
| $   | A+B+C+D+E | 
|-----|-----------|
| 100 |     7     |
| 200 |     12    |
| 300 |     17    |
| 400 |     21    | 
| 500 |     26    |

500ABCD = 400ABC + 100D = 100AB + 300C + 100D = ***100B + 300C + 100D = 5 + 14 + 7 = 26***

### ***Ответ:*** максимально возможная сумма прибыли = 26, если распределить инвестиции следующим образом 
100$ в проект B  
300$ в проект C  
100$ в проект D