---
title: python script multiprocessing pi (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multiprocessing pi'

Functions in program: 
* `def main():`
* `def generate_random(q, count):`
* `def reduce_d(count_inside, d):`
* `def map_d(c):`

Modules used in program: 
* `import multiprocessing`
* `import math`
* `import random`
* `import functools`

## python multiprocessing pi

Python mysql example: multiprocessing pi

```python
import functools
import random
import math
import multiprocessing


def map_d(c):
    return math.hypot(random.random(), random.random())


def reduce_d(count_inside, d):
    if d < 1:
        return count_inside + 1

    return count_inside


def generate_random(q, count):
    d_list = map(map_d, range(0, count))
    count_inside = functools.reduce(reduce_d, d_list)
    q.put(count_inside)


def main():
    count = 100000000
    cores = 4
    q = multiprocessing.Queue(maxsize=cores)

    for i in range(cores):
        p = multiprocessing.Process(target=generate_random, args=(q, int(count/cores)))
        p.start()

    count_inside = 0
    for _ in range(cores):
        count_inside += q.get()

    print(4.0 * count_inside / count)


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
