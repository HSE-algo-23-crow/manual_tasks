### Условия задачи для Mongolian Tomatoes:
  
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
## Решение

	1. Вывод рекуррентного соотношения
Выпишем элементы матрицы:	 a = -14; b = 2; c = 24

Рекуррентное соотношение для данной матрицы:

$$
det A_n =  -14 \cdot  det A_{n-1} - 48 \cdot  det A_{n-2} 
$$    

	2. Составление характеристического уравнения и его решение:
$$
t^2 + 14t + 48 = 0
$$  

 $$
t_{1}=-6;  t_{2}=-8
$$

$$
t_{1}\neq t_{2}
$$

	3. Вывод формулы общего решения
Поскольку корни не равны, то составляем рекуррентное соотношение: 

$$
det A_n =  C_1\cdot(-6)^n+C_2\cdot(-8)^n
$$    

Найдем определители 1 и 2 порядка:

$$
det _1 = -14
$$    

$$
det _2 = 148
$$ 

Подставляем корни в систему:

$$ 
\left\{ \begin{array}{ll} 
-14 = -6 \cdot C_1-8 \cdot C_2\\
148=36 \cdot C_1+64 \cdot C_2  
\end{array}\right.  $$

$$ 
\left\{ \begin{array}{ll} 
-84 = -36 \cdot C_1+(-48) \cdot C_2\\
148=36 \cdot C_1+64 \cdot C_2  
\end{array}\right.  $$

$$
64 = 16\cdot C_2
$$

$$
C_1=-3; C_2=4 
$$

Таким образом, общая формула определителя ленточной матрицы:

$$
det A_n =  -3\cdot(-6)^n+4\cdot(-8)^n
$$   
 
	4. Значение определителя матрицы  n = 13 порядка
 
$$
-3\cdot(-6)^{13}+4\cdot(-8)^{13} =-2159841173504
$$
