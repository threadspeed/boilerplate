---
title: python script Ds al (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ds al'

Functions in program: 
* `def f_print(x):`
* `def f_none(x):`
* `def f(x):`

Modules used in program: 
* `import time`

## python Ds al

Python example: Ds al

```python
from multiprocessing import Pool
import time

def f(x):
    for i in range(10**x):
        i

def f_none(x):
    pass

def f_print(x):
    for i in range(10**x):
        print(i)

if __name__ == '__main__':
    # 싱글쓰레드 구성
    start = time.time()
    f(7)
    f(7)
    print(time.time() - start)

    # 멀티쓰레드 구성
    start = time.time()
    Pool(2).map(f, (7, 7)) # 자식프로세스를 2개 생성하여, 각각 f(7)을 수행한다.
    print(time.time() - start)

    # 멀티쓰레드 구성 – overhead 측정
    start = time.time()
    Pool(2).map(f_none, (0, 0)) # f_none을 수행한다.
    print(time.time() - start)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
