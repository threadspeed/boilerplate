---
title: python script week 007 book search (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 007 book search'

Functions in program: 
* `def book_search():`

Modules used in program: 
* `import random`

## python week 007 book search

Python example: week 007 book search

```python
import random

def book_search():
    racks = random.randint(5, 20)
    print("Стеллажей в магазине: %d" % racks)
    
    true_rack = random.randint(1, racks)
    true_shelf = random.randint(1, 5)

    print("Искомая книга находится на стеллаже № %d и полке № %d.)" % (true_rack, true_shelf))
    print("Но Таня об этом еще не знает...\n")

    true_book = 0       # номер "той самой книиги" нам пока неизвестен
    i_rack = 1          # начинаем со стеллажа № 1
    success = False     # к успеху пока не пришли 
    
    while i_rack <= racks and not success:
        print("Таня проверяет стеллаж № %d" % i_rack)

        if i_rack != true_rack:     # пропустить заведомо неподходящий стеллаж с вероятностью 16%
            if random.randint(1, 100) <= 16:
                print("Это явно не то! Таня пропускает этот стеллаж")
                i_rack += 1
                continue

        i_shelf = 1     # начинаем с полки № 1 
        while i_shelf <= 5 and not success:
            print("\tТаня проверяет полку № %d" % i_shelf)

            nbooks = random.randint(9, 33)      # генерируем число книжек на данной полке

            if i_shelf == true_shelf and i_rack == true_rack:       # если это нужные нам стеллаж и полка, генерируем номер "той самой" книги
                true_book = random.randint(1, nbooks)
            elif random.randint(1, 1000) <= 395:                    # пропуск заведомо неподходящей полки
                print("Фи! Таня пропускает эту полку!")
                i_shelf += 1
                continue

            i_book = 1      # начинаем с книги № 1
            while i_book <= nbooks:
                print("\t\tТаня листает книгу № %d" % i_book)

                if i_book != true_book:     # если это не та книга, смотрим следующую
                    i_book += 1
                    continue
                else:                       # если находим нужную книгу, выходим из текущего цикла и меняем значение переменной success, чтобы выйти из других циклов
                    print("Ура! Таня нашла подходящую книгу! Ей оказалась книга № %d" % i_book)
                    success = True
                    break

            i_shelf += 1
        i_rack += 1

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
