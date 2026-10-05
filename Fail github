# %% задание 1.1.
~~~
a = 6
b = 7
c = a * b
print(c)
~~~

# %% задание 1.2.
~~~
x = 10 ** 100000
print(x)
~~~

# %% задание 1.3.
~~~
a, b = divmod(10, 3) #показывает одновременно 2 значения
print(a)
print(b)
~~~

# %% задание 1.4.
~~~
a = 10
while a != 0:
    a -= 0.1 #проблема в 0.1, компьютер хранит числа с плавающей точкой в двоичном виде, а 0.1 нельзя представь в двоичной системе
~~~

# %% задание 1.5.
~~~
z = 1
z <<= 40
2 ** z
# программа не зависла, она обрабатывает очень большое число
~~~

# %% Задание 1.6.
~~~
i = 0
while i < 10:
    print(i)
    ++i # в питоне нет оператора ++, поэтому все рвемя i == 0
#   i += 1 #правильно так
~~~

# %% Задание 1.7.
~~~
(True * 2 + False) * -True
#True ==1, False == 0. значит (1 * 2 + 0) * (-1) = -2
~~~

# %% Задание 1.8.
~~~
x = 5
1 < x < 10 #верно 1 < 5 - True, 5 < 10 - True, True и True

x = 5
1 < (x < 10) #5 < 10 = True=1, 1 < 1 = False 
~~~

# %% Задание 2.1.SyntaxError: invalid syntax
~~~
if x = 5:
    print(x) #ошибка, потому что в условии нельзя писать =, надо ==
~~~

# %% Задание 2.2.SyntaxError: cannot assign to literal
~~~
5 = x #ошибка, нельзяприсвоить значение числу
~~~

# %% Задание 2.3.NameError: name ... is not defined
~~~
print(x) #ошибка, не был создан x 
~~~

# %% Задание 2.4. SyntaxError: unterminated string literal
~~~
#print("Привет) # ошибка, не хватает кавычек
~~~

# %% Задание 2.5. TypeError: unsupported operand type(s) for ...
~~~
x = "5" + 2 #ошибка, 5 не число
~~~

# %% Задание 2.6. IndentationError: expected an indented block
~~~
if True:
print("Привет") #нет отступа после if
~~~

# %% Задание 2.7. IndentationError: unindent does not match any outer indentation level
~~~
if True:
    print("Первая строка")
  print("Вторая строка") #неправильный отступ
~~~

# %% Задание 2.8. ValueError: math domain error
~~~
import math
print(math.sqrt(-1)) # не умеет брать квадратныйкорень из отрицательного числа
~~~

# %% Задание 2.9. OverflowError: math range error
~~~
import math
print(math.exp(1000)) #пытается вычислить очень большое число, которое не помещается
~~~

# %% 3.1.
~~~
x = 1
a = x + x      
b = a + a      
c = b + b      
result = c + b 
print(result)
~~~

# %% 3.2.
~~~
x = 1
a = x + x
b = a + a
c = b + b
result = c + c
print(result)
~~~

# %% 3.3.
~~~
x = 1
a = x + x
b = a + a
c = b + b
d = x - c
result = c - d
print(result)
~~~

# %% 3.4. исправление ошибок
~~~
import random #включает модуль для генерациислучайных чисел
def naive_mul(x, y): #функция, кот. умножает 2 числас помощью сложения
    r = 0; #переменная. результат должен начинаться с 0
    for i in range(0, y):
        r = r + x; #при каждом повторении цикла прибавляем число x к текущемурезультату r
    return r #возвращает полученный результатдля сипользования;оператора end в питоне нет


for i in range(100): # 100 проверок
        x = random.randint(0, 100) #генерим случайное число 
        y = random.randint(0, 100)

        assert naive_mul(x, y) == x * y #проверяет правильно ли работает функция
        
print("Все тесты пройдены!")
~~~

# %% 3.5.
~~~
import random
def fast_mul(x, y): #def - команда создания функции,
     result = 0

     while x > 0: #повторяет действия пока х > 0
          if x % 2 == 1: #% остаток деления (нечет). == проверка равенства
               result = result + y

          x = x // 2 # // целочисленное деление
          y = y * 2

     return result

for i in range(100):
     x = random.randint(0, 100)
     y = random.randint(0,100)

     assert fast_mul(x, y) == x * y #умножаем числа функции, assert проверяем одинаковые результаты

     print(x, "*", y, "=", fast_mul(x, y)) #водим на экран числа и результат умножения

print("Все тесты пройдены")
~~~

# %% 3.6.
~~~
import random

def fast_pow(x, y):
     result = 1

     while y > 0:
          if y % 2 == 1:
               result = result * x

          x = x ** 2
          y = y // 2
     return result

for i in range(100):
        x = random.randint(0, 100)
        y = random.randint(0, 100)

        assert fast_pow(x, y) == x ** y 
        
        print(x, "*", y, "=", fast_pow(x, y)) 
        
        print("Все тесты пройдены") 
~~~

# %% 3.7
~~~
def mul_bits(x, y, bits): #bits сколько бит разрешеноиспользовать для представления каждого числа
    x &= (2 ** bits - 1) #2 ** bits возведение двойки в степени bits
    y &= (2 ** bits - 1)
    return x * y

def mul16(x, y):
     a = x & 255 #оставляет только последние 8 бит числа x
     b = x >> 8

     c = y & 255
     d = y >> 8

     p1 = mul_bits(a, c, 8)
     p2 = mul_bits(a, d, 8)
     p3 = mul_bits(b, c, 8)
     p4 = mul_bits(b, d, 8)

     result = p1 + (p2 << 8) + (p3 << 8) + (p4 << 16) #xy=ac+256ad+256bc+65536bd
     return result

print(mul16(1000, 2000))
~~~

# %% 3.8
~~~
def mul_bits(x, y, bits): #bits сколько бит разрешеноиспользовать для представления каждого числа
    x &= (2 ** bits - 1) #2 ** bits возведение двойки в степени bits
    y &= (2 ** bits - 1)
    return x * y

def mul16k(x, y):
     a = x & 255 #оставляет только последние 8 бит числа x
     b = x >> 8

     c = y & 255
     d = y >> 8

     p1 = mul_bits(a, c, 8)
     p2 = mul_bits(b, d, 8)
     p3 = mul_bits(a + b, c + d, 9)
    

     result = p1 + ((p3-p1-p2)<< 8) + (p2 << 16) #xy=ac+256(ad+bc)+65536bd
     return result

print(mul16k(1000, 2000))
~~~

# %% 4.1. Черный квадрат
~~~
import math
import tkinter as tk


def draw(shader, width, height):
    image = bytearray((0, 0, 0) * width * height)
    for y in range(height):
        for x in range(width):
            pos = (width * y + x) * 3
            color = shader(x / width, y / height)
            normalized = [max(min(int(c * 255), 255), 0) for c in color]
            image[pos:pos + 3] = normalized
    header = bytes(f'P6\n{width} {height}\n255\n', 'ascii')
    return header + image
def main(shader):
    label = tk.Label()
    img = tk.PhotoImage(data=draw(shader, 256, 256)).zoom(2, 2)
    label.pack()
    label.config(image=img)
    tk.mainloop()
def shader(x, y):
    return 0, 0, 0
main(shader)
~~~

# %% 4.2. Шар
~~~
import math
import tkinter as tk
def draw(shader, width, height):
    image = bytearray((0, 0, 0) * width * height)
    for y in range(height):
        for x in range(width):
            pos = (width * y + x) * 3
            color = shader(x / width, y / height)
            normalized = [max(min(int(c * 255), 255), 0) for c in color]
            image[pos:pos + 3] = normalized
    header = bytes(f'P6\n{width} {height}\n255\n', 'ascii')
    return header + image
def main(shader):
    label = tk.Label()
    img = tk.PhotoImage(data=draw(shader, 256, 256)).zoom(2, 2)
    label.pack()
    label.config(image=img)
    tk.mainloop()
def shader(x, y):
    dx = x - 0.5
    dy = y - 0.5
    distance = math.sqrt(dx * dx + dy * dy)
    brightness = max(0, 1 - distance * 3)
    red = brightness
    green = brightness * (1 - x)
    blue = 0
    return red, green, blue
main(shader)
~~~
