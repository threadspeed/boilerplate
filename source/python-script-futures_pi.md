---
title: python script futures pi (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'futures pi'

Functions in program: 
* `def main():`
* `def generate_random(count):`
* `def reduce_d(count_inside, d):`
* `def map_d(c):`

Modules used in program: 
* `import math`
* `import random`
* `import functools`

## python futures pi

Python example: futures pi

```python
import functools
import random
import math
from concurrent import futures


def map_d(c):
    return math.hypot(random.random(), random.random())


def reduce_d(count_inside, d):
    if d < 1:
        return count_inside + 1

    return count_inside


def generate_random(count):
    d_list = map(map_d, range(0, count))
    count_inside = functools.reduce(reduce_d, d_list)
    return count_inside


def main():
    count = 100000000
    cores = 4
    count_inside = 0

    with futures.ProcessPoolExecutor(cores) as executor:
        for val in executor.map(generate_random, (int(count/cores) for _ in range(cores)) ):
            count_inside += val

    print(4.0 * count_inside / count)


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
