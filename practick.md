# Практика


# %% задача 3. Единицы измерения информации
~~~
kb = 2 ** 10 #2 в степени 10
mb = 2 ** 20
gb = 2 ** 30
tb = 2 ** 40
print("1 Кбайт =", kb, "байт")
print("1 Мбайт =", mb, "байт")
print("1 Гбайт =", gb, "байт")
print("1 Тбайт =", tb, "байт")
~~~

# %% задача 4. Объём сообщения в битах и байтах
~~~
text = "Привет, информатика!"
n = len(text) #возвращает длину строки
print("Количество символов", n) 

bits = n * 8
print("Объём сообщения", bits)
~~~

# %% задача 5. Частная энтропия одного события
~~~
import math #подключаем переменную
p = 0.25
I = math.log2(1 / p) #формула
print(I)
~~~

# %% задача 6. Энтропия Шеннона для источника
~~~
import math

def entropy(p):
    H = 0
    for prob in p:
        H = H - prob * math.log2(prob)
    return H
print(entropy(p = [0.5, 0.5]))
~~~

# %% задача 7. Энтропия двоичного источника
~~~
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
~~~

# %% задача 8. Фильтрация — убираем «шум»
~~~
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
~~~

# %% Задача 10. Сбор и формализация данных
~~~
spisok1 = ["иванов", "ПЕТРОВ", "сидоров"]
spisok2 = ["кузнецов", "СМИРНОВ"]
families = spisok1 + spisok2
print(families)
result = [x.capitalize() for x in families] #capitalize приводит список к единому формату
print(result)
~~~

# %% Задача 11. Девять свойств информации
~~~
svoystva = [
    "объективность",
    "достоверность",
    "полнота",
    "точность",
    "актуальность",
    "полезность",
    "своевременность",
    "понятность",
    "краткость"]
for number, name in enumerate(svoystva, start=1): #нумерует, начало с 1
    print(number, name)
~~~

# %% Задачи 12 не было в файле.

# %% Задача 13. Параллельная сортировка массива
~~~
massiv = [8, 3, 5, 1, 9, 2, 7, 4]
seredina = len(massiv) // 2
levaya = massiv[:seredina]
pravaya = massiv[seredina:]
levaya_sort = sorted(levaya)
pravaya_sort = sorted(pravaya)
print(levaya_sort)
print(pravaya_sort)
def merge(left, right):
    result = []
    i = 0
    j = 0
    while i < len(left) and j < len(right):
         if left[i] < right[j]:
             result.append(left[i])
             i = i + 1
         else: 
             result.append(right[j])
             j = j + 1
    result.extend(right[j:])
    result.extend(left[i:])
    return result
print(merge(levaya_sort, pravaya_sort))
~~~
