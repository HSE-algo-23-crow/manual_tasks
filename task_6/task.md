
# Вычисление ленточного определителя (трехдиагональной матрицы)  
В условиях задачи для каждой команды указана трехдиагональная матрица порядка *n*. Для решения задачи требуется:  
1. Вывести рекуррентное соотношение для предложенной матрицы.  
2. Составить и решить характеристическое уравнение.  
3. Вывести формулу общего решения.  
4. Рассчитать на основе полученной формулы значение определителя матрицы порядка *n*.  
## Условия задачи для команд:
### Yes Team:

$$    
A =     
 \begin{pmatrix}    
  6 & 2 & 0 & \cdots & 0 & 0 \\    
  4 & 6 & 2 & \cdots & 0 & 0 \\    
  0 & 4 & 6 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & 6 & 2 \\    
  0 & 0 & 0 & \cdots & 4 & 6     
 \end{pmatrix}    
$$

Порядок матрицы *n* = 8

### Gigacode Team:

$$    
A =     
 \begin{pmatrix}    
  14 & 7 & 0 & \cdots & 0 & 0 \\    
  7 & 14 & 7 & \cdots & 0 & 0 \\    
  0 & 7 & 14 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & 14 & 7 \\    
  0 & 0 & 0 & \cdots & 7 & 14     
 \end{pmatrix}    
$$

Порядок матрицы *n* = 9

### citrine Team:

$$    
A =     
 \begin{pmatrix}    
  -16 & 2 & 0 & \cdots & 0 & 0 \\    
  30 & -16 & 2 & \cdots & 0 & 0 \\    
  0 & 30 & -16 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & -16 & 2 \\    
  0 & 0 & 0 & \cdots & 30 & -16     
 \end{pmatrix}    
$$

Порядок матрицы *n* = 10

### ALTYN Team:

$$    
A =     
 \begin{pmatrix}    
  -4 & 1 & 0 & \cdots & 0 & 0 \\    
  4 & -4 & 1 & \cdots & 0 & 0 \\    
  0 & 4 & -4 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & -4 & 1 \\    
  0 & 0 & 0 & \cdots & 4 & -4     
 \end{pmatrix}    
$$

Порядок матрицы *n* = 11

### Mysterious:

$$    
A =     
 \begin{pmatrix}    
  -2 & -3 & 0 & \cdots & 0 & 0 \\    
  21 & -2 & -3 & \cdots & 0 & 0 \\    
  0 & 21 & -2 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & -2 & -3 \\    
  0 & 0 & 0 & \cdots & 21 & -2     
 \end{pmatrix}    
$$

Порядок матрицы *n* = 12

### Mongolian tomatoes:

$$    
A =     
 \begin{pmatrix}    
  -14 & 2 & 0 & \cdots & 0 & 0 \\    
  24 & -14 & 2 & \cdots & 0 & 0 \\    
  0 & 24 & -14 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & -14 & 2 \\    
  0 & 0 & 0 & \cdots & 24 & -14     
 \end{pmatrix}    
$$

Порядок матрицы *n* = 13

### CommitIT:

$$    
A =     
 \begin{pmatrix}    
  -12 & 8 & 0 & \cdots & 0 & 0 \\    
  4 & -12 & 8 & \cdots & 0 & 0 \\    
  0 & 4 & -12 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & -12 & 8 \\    
  0 & 0 & 0 & \cdots & 4 & -12     
 \end{pmatrix}    
$$

Порядок матрицы *n* = 12

### Girls:

$$    
A =     
 \begin{pmatrix}    
  1 & -1 & 0 & \cdots & 0 & 0 \\    
  2 & 1 & -1 & \cdots & 0 & 0 \\    
  0 & 2 & 1 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & 1 & -1 \\    
  0 & 0 & 0 & \cdots & 2 & 1     
 \end{pmatrix}    
$$

Порядок матрицы *n* = 11

### GetBrains:

$$    
A =     
 \begin{pmatrix}    
  6 & 1 & 0 & \cdots & 0 & 0 \\    
  5 & 6 & 1 & \cdots & 0 & 0 \\    
  0 & 5 & 6 & \cdots & 0 & 0 \\    
  \vdots  & \vdots & \vdots & \ddots & \vdots & \vdots  \\    
  0 & 0 & 0 & \cdots & 6 & 1 \\    
  0 & 0 & 0 & \cdots & 5 & 6     
 \end{pmatrix}    
$$

Порядок матрицы *n* = 10
