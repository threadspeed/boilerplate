---
title: python script memreadhton3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'memreadhton3'

Functions in program: 
* `def bench(length):`

Modules used in program: 
* `import time`
* `import random`

## python memreadhton3

Python mysql example: memreadhton3

```python
import random
import time


def bench(length):
    data = list(range(int(length)))
    ordererdidx = list(range(int(length)))
    randomidx = list(range(int(length)))
    random.shuffle(randomidx)
    j = 0
    start = time.time()
    for i in range(int(length)):
        j = data[ordererdidx[i]]
    p1 = time.time() - start
    start = time.time()
    for i in range(int(length)):
        j = data[randomidx[i]]
    p2 = time.time() -start

    print("%d, %.20f,  %.20f" % (length, p1, p2))



for i in range(2,9):
    bench((10**i)/2)
    bench(10**i)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
