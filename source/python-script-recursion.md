---
title: python script recursion (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'recursion'

Functions in program: 
* `def fib(n):`
* `def factorial(n):`
* `def power(x, n):`

## python recursion

Python mysql example: recursion

```python
### Рекурсия

'''
Рекурсивная функция - это такая функция, которая вызывает саму себя.
С рекурсией надо быть очень осторожными. Если мы не будем внимательными, цепочка вызовов функцией самой себя окажется бесконечной.

Поэтому если уж вы пишете рекурсивную функцию, надо:
1) не забывать прописывать то, что называется выходом из рекурсии (то есть те условия, при которых нам надо остановиться)
2) всегда следить за тем, что последовательность вызовов функцией самой себя будет конечной

Давайте воспользуемся рекурсией для того, чтобы решить простые математические задачки
(решать их с помощью рекурсии - не более, чем упражнение в программировании, не надо думать, что подобный вариант решения - хороший)
'''

### Степень числа

'''
Задача: написать рекурсивную функцию, которая возводит число x в натуральную степень n.

Допустим, мы уже научились возводить x в степень (n-1). Как в таком случае вычислить x в степени n?
x^n = x * x^(n-1)
Логично?
Это значит, что мы можем свести задачу нахождения x в степени n к задаче нахождения x в степени n-1.
Но как тогда найти x^(n-1)?
Аналогично: x^(n-1) = x * x^(n-2)

И так далее...

x^3 = x * x^2
x^2 = x * x^1
x^1 = x * x^0

Вот тут нам бы остановиться, не так ли? Как мы знаем, x^0 для любого x равно 1.
Значит для всех n, не равных нулю, мы будем использовать формулу x^n = x * x^(n-1), а для n == 0 нам надо будет самим прописать, что функция должна возвращать.

'''

def power(x, n):
    print("Сейчас вызываем power от", x, "и", n) # для того, чтобы понимать, что происходит
    if n != 0:
        return x * power(x, n - 1) # x^n = x * x^(n-1)
    else:
        return 1 # в случае, если возводим в 0 степень, то возвращаем 1

power(2, 5)
power(10, 3)

'''
Давайте поймем, почему функция работает.
Допустим, вы вызываете power(10, 3). Что происходит? Посмотрите, что выводит вам print(на экран.)
Всего у нас получается 4 вызова функции (один - наш, три остальных раза наша функция сама себя вызывает).
Что изменяется при этих вызовах? Степень: 3, 2, 1, 0
Всегда ли такая последовательность рекурсивных вызовов функции будет конечной? Да, n - натуральное число, и на каждом шаге мы вычитаем из него 1, рано или поздно мы дойдем до 0.

power(10, 3) = 10 * power(10, 2) = 10 * 10 * power(10, 1) = 10 * 10 * 10 * power(10, 0) = 10 * 10 * 10 * 1 = 1000

'''

### Факториал числа

'''
Задача: написать рекурсивную функцию, которая вычисляет факториал числа n.
Факториалом числа n (обозначается n!) называется произведение чисел от 1 до n. Факториал нуля по определению равен единице.

Рассуждение аналогично тому, которое мы использовали в задаче со степенью: допустим, что мы уже умеем находить факториал (n-1).
Как в таком случае найти факториал n?

n! = (n-1)! * n

Это значит, что для того, чтобы вычислить факториал n, надо сначала вычислить факториал (n-1), а затем домножить то, что получилось, на n.
Хорошо, но как найти факториал (n-1)? Надо вычислить факториал (n-2) и затем умножить его на (n-1).
Хорошо, но как...
Когда надо остановиться?
Когда мы попытаемся посчитать факториал 1, получим, что 1! = 1 * 0!
0! по определению равен 1.
Вывод: для всех n, не равных 0, мы можем вычислить значение факториала n по формуле n! = (n-1)! * n, но для 0 это невозможно - тут его значение нам надо определить самим.
'''

def factorial(n):
    print("Сейчас вызываем factorial от", n) # для того, чтобы понимать, что происходит
    if n != 0:
        return n * factorial(n - 1) # функция вызывает сама себя, но от числа на 1 меньше
    else:
        return 1 # факториал нуля по определению равен 1

factorial(5)
factorial(3)

'''
factorial(3) = 3 * factorial(2) = 3 * 2 * factorial(1) = 3 * 2 * 1 * factorial(0) = 3 * 2 * 1 * 1
'''

### Числа Фибоначчи
# 0, 1, 1, 2, 3, 5, 8, 13, 21, ...

'''
Числа Фибоначчи это последовательность чисел, каждое из которых является суммой двух предыдущих. По определению нулевое число Фибоначчи равно 0, первое - 1.
Ниже приведена функция, которая считает n-ное число Фибоначчи четко по определению.
Примечание: такая функция наглядна и помогает понять, что представляет из себя рекурсия, но работает она оооооочеь медленно (посмотрите на количество вызовов функцией самой себя и ужаснитесь).
'''

def fib(n):
    print("Сейчас вызываем fib от", n)
    if n > 1:
        return fib(n-1) + fib(n-2)
    else:
        return n

fib(1)
fib(2)
fib(3)
fib(7)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com