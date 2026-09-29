# задание 1

~~~
gggggg
~~~
# %% задача 3. Единицы измерения информации
kb = 2 ** 10 #2 в степени 10
mb = 2 ** 20
gb = 2 ** 30
tb = 2 ** 40
print("1 Кбайт =", kb, "байт")
print("1 Мбайт =", mb, "байт")
print("1 Гбайт =", gb, "байт")
print("1 Тбайт =", tb, "байт")

# %% задача 4. Объём сообщения в битах и байтах
text = "Привет, информатика!"
n = len(text) #возвращает длину строки
print("Количество символов", n) 

bits = n * 8
print("Объём сообщения", bits)

# %% задача 5. Частная энтропия одного события
import math #подключаем переменную
p = 0.25
I = math.log2(1 / p) #формула
print(I)

# %% задача 6. Энтропия Шеннона для источника
import math

def entropy(p):
    H = 0
    for prob in p:
        H = H - prob * math.log2(prob)
    return H
print(entropy(p = [0.5, 0.5]))

# %% задача 7. Энтропия двоичного источника
import math

def entropy(p): #создали функцию
    H = 0 #переменная
    for prob in p: # для prob в p
        if prob > 0: #если prob больше 0
            H = H -prob * math.log2(prob) #тогда 
    return H
print(entropy([0.9, 0.1])) #энтропия для первого числа равна 90 %, для второго 10%
print(entropy([0.5, 0.5]))
print(entropy([1.0, 0])) #нет энтропии

# %% задача 8. Фильтрация — убираем «шум»
dannye = [12, -1, 45, 0, 78, -5, 33]

result = [x for x in dannye if x > 0] # убирает те, которые  больше 0
print("было:", dannye)
print("Стало:", result)

# %% задача 9. Сортировка данных
bally = [34, 89, 5, 56, 12]
vozrastanie = sorted(bally) #сортировка на возрастание
print(vozrastanie)
ubyvanie = sorted(bally, reverse=True) # reverse=True включает сортировку на убывание
print(ubyvanie)

# %% Задача 10. Сбор и формализация данных
spisok1 = ["иванов", "ПЕТРОВ", "сидоров"]
spisok2 = ["кузнецов", "СМИРНОВ"]
families = spisok1 + spisok2
print(families)
result = [x.capitalize() for x in families] #capitalize приводит список к единому формату
print(result)

#gihub
a = 1
b = a + a #2
c = b + b #4
d = c + c #8
e = a - d #-7
f = d - e
print(f)

# %% 3.4. исправление ошибок
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

# %% 3.5.
import random
def fast_mul(x, y): #def - команда создания функции,
     result = 0

     while x > 0: #повторяй действия пока х > 0
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
     
# %% 3.6.

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


# %% 3.7

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

# %% 3.8
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

# %% 3.9. 


