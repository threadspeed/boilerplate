---
title: python script memreadhton2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'memreadhton2'

Functions in program: 
* `def bench(length):`

Modules used in program: 
* `import time`
* `import random`

## python memreadhton2

Python example: memreadhton2

```python
import random
import time


def bench(length):
    data = range(length)
    ordererdidx = range(length)
    randomidx = range(length)
    random.shuffle(randomidx)
    j = 0
    start = time.time()
    for i in range(length):
        j = data[ordererdidx[i]]
    p1 = time.time() - start
    start = time.time()
    for i in range(length):
        j = data[randomidx[i]]
    p2 = time.time() -start

    print("%d \t %.20f \t %.20f" % (length, p1, p2))



for i in range(2,9):
    bench((10**i)/2)
    bench(10**i)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
