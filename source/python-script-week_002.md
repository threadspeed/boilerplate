---
title: python script week 002 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 002'

Functions in program: 
* `def hour_min(n):`
* `def f3(x):`
* `def f2(x):`
* `def f1(x):`
* `def calc(x1, x2, x3):`
* `def see_stars(n):`
* `def count_hundreds(x):`
* `def pcnt (a, b, d):`
* `def distance(velocity, time):`
* `def tri_print(s):`
* `def lets_check(n):`

## python week 002

Python mysql example: week 002

```python
# HW week 2

def lets_check(n):
    print("\nLet's check № %d!" % n)

# 1

def tri_print(s):
    print((s + " ") * 3)

lets_check(1)
your_str = input("Enter a string: ")

tri_print(your_str)

# 2

def distance(velocity, time):
    result = velocity * time
    return result

lets_check(2)
your_velocity = int(input("Enter a velocity argument: "))
your_time = int(input("Enter a time argument: "))

print(distance(your_velocity, your_time))

# 3

def pcnt (a, b, d):
    result = (a / b) * 100
    result = round(result, d)
    print(result, "%")

lets_check(3)
your_a = int(input('Enter a number (a): '))
your_b = int(input('Enter a number (b): '))
your_d = int(input('Enter a number (d): '))

pcnt(your_a, your_b, your_d)

# 4

def count_hundreds(x):
    result = x // 100
    return result

lets_check(4)
your_x = int(input('Enter a number: '))

print(count_hundreds(your_x))

# 5

def see_stars(n):
    print("*" * n)

lets_check(5)
your_n = int(input("Enter a number of stars: "))

see_stars(your_n)

# HW week 2.1

# 1

def calc(x1, x2, x3):
    result = (x1 + x2) * x3
    print(result)

lets_check(1)
your_x1 = int(input("Enter a number (x1): "))
your_x2 = int(input("Enter a number (x2): "))
your_x3 = int(input("Enter a number (x3): "))

calc(your_x1, your_x2, your_x3)

# 2

def f1(x):
    return x // 3

def f2(x):
    return f3(x)

def f3(x):
    print("Результат:", x)

lets_check(2)
your_x = int(input("Enter a number: "))

f2(f1(your_x))

# 3 (that wasn't there)

def hour_min(n):
    hours = n // 60
    mins = n % 60
    print(("%d ч. %d м." % (hours, mins)))

lets_check(3)
your_n = int(input("Enter a number of minutes: "))

hour_min(your_n)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
