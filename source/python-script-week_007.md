---
title: python script week 007 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 007'

Functions in program: 
* `def pine_tree(n, s = "*"): # Не работает на других n`
* `def rhombus_hole(n, h, s = "*"): # h - высота/ширина отверстия (нечетная)`
* `def row_hole(i, n, h, s):`
* `def rhombus(n, s = "*"):`
* `def pyramid(n, s = "*"):`
* `def row(i, n, s):`
* `def wrap_in(text, sym):`
* `def right_alignment(n, s = "*"):`
* `def left_alignment(n, s = "*"):`
* `def reverse_hillside(n, s = "*"):`
* `def hillside(n, s = "*"):`
* `def square(n, s = "*"):`

## python week 007

Python example: week 007

```python
# 0

def square(n, s = "*"):
    s += " "
    for i in range(n):
        print(s * n)

square(10)

# 1

def hillside(n, s = "*"):
    s += " "
    for i in range(1, n + 1):
        print(s * i)

hillside(10)
    
# 2

def reverse_hillside(n, s = "*"):
    s += " "
    for i in range(1, n + 1):
        print('  ' * (n - i) + s * i)

reverse_hillside(10)

# 3

def left_alignment(n, s = "*"):
    s += " "
    for i in range(n, 0, -1):
        print(s * i)

left_alignment(10)

# 4

def right_alignment(n, s = "*"):
    s += " "
    for i in range(n):
        print('  ' * i + s * (n - i))

right_alignment(10)

# 5

def wrap_in(text, sym):
    return sym + text + sym

def row(i, n, s):
    print(wrap_in(s * (2 * i - 1),
                      '  ' * (n - i)))

def pyramid(n, s = "*"):
    s += " "
    for i in range(1, n + 1):
        row(i, n, s)
        # print('  ' * (n - i) + s * (2 * i - 1) + '  ' * (n - i))

pyramid(10)

# 6

def rhombus(n, s = "*"):
    pyramid(n)
    s += " "
    for i in range(n - 1, 0, -1):
        row(i, n, s)

rhombus(10)

# 7

def row_hole(i, n, h, s):
    m = ((2 * n - 1) - h) // 2
    if i <= m:
            row(i, n, s)
    else:
        empt = (i - m) * 2 - 1
        print(wrap_in(wrap_in('  ' * empt, s * m),
                  '  ' * (n - i)))

def rhombus_hole(n, h, s = "*"): # h - высота/ширина отверстия (нечетная)
    s += " "
    for i in range(1, n + 1):
        row_hole(i, n, h, s)
    for i in range(n - 1, 0, -1):
        row_hole(i, n, h, s)

rhombus_hole(10, 7)

# 8

def pine_tree(n, s = "*"): # Не работает на других n
    s += " "
    for i in range(1, 4):
        for j in range(i // 2 + 1, i + 3):
            print(wrap_in(s * (2 * j - 1),
                          "  " * (((n - 1) - (2 * j - 1)) // 2)))

pine_tree(10)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
