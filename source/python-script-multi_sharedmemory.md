---
title: python script multi sharedmemory (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multi sharedmemory'

Functions in program: 
* `def main():`
* `def f(start, stop, a):`

Modules used in program: 
* `import random`

## python multi sharedmemory

Python example: multi sharedmemory

```python
from multiprocessing import Process, Value, Array
import random


def f(start, stop, a):
    for i in xrange(start, stop):
        a[i] = random.randint(0, 10)

def main():
    arr = Array('i', 1000000)
    s = 1000000
    count = 2
    forproc = s/2
    jobs = []
    start = 0
    stop = start + forproc
    for i in xrange(count):
        p = Process(target=f, args=(start, stop, arr))
        p.start()
        jobs.append(p)
        start, stop = stop, stop + forproc

    for job in jobs:
        job.join()

    print(len(arr))

if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
