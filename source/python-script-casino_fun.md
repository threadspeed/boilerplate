---
title: python script casino fun (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'casino fun'

Functions in program: 
* `def experiment():`
* `def sim(pool, goal, bet, k, win_rate):`
* `def experiment():`
* `def sim(pool, goal, bet, k, win_rate):`

Modules used in program: 
* `import random`
* `import random`

## python casino fun

Python mysql example: casino fun

```python
import random


def sim(pool, goal, bet, k, win_rate):
    init_pool = pool
    for i in range(0, k):
        if pool == 0:
            return -2
        pool = pool - bet
        roll = random.random()
        if roll < win_rate:
            pool = pool + bet*2
            if pool >= goal:
                return 2
    if pool >= init_pool:
        return 1
    return -1


def experiment():
    list = []
    for j in range(0, 200000):
        val = sim(100000, 101000, 1000, 100, 0.50)
        list.append(val)

    print(list.count(2))
    print(list.count(1))
    print(list.count(-1))
    print(list.count(-2))
    print((list.count(-1) + list.count(-2)) / (list.count(2) + list.count(1)))

experiment()
import random


def sim(pool, goal, bet, k, win_rate):
    init_pool = pool
    for i in range(0, k):
        if pool == 0:
            return -2
        pool = pool - bet
        roll = random.random()
        if roll < win_rate:
            pool = pool + bet*2
            if pool >= goal:
                return 2
    if pool >= init_pool:
        return 1
    return -1


def experiment():
    list = []
    for j in range(0, 200000):
        val = sim(100000, 101000, 1000, 100, 0.50)
        list.append(val)

    print(list.count(2))
    print(list.count(1))
    print(list.count(-1))
    print(list.count(-2))
    print((list.count(-1) + list.count(-2)) / (list.count(2) + list.count(1)))

experiment()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
