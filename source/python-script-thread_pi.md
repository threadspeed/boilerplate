---
title: python script thread pi (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'thread pi'

Functions in program: 
* `def main():`
* `def generate_random(q, count):`
* `def reduce_d(count_inside, d):`
* `def map_d(c):`

Modules used in program: 
* `import threading`
* `import math`
* `import random`
* `import functools`
* `import queue`

## python thread pi

Python example: thread pi

```python
import queue
import functools
import random
import math
import threading


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
    threads = 4
    q = queue.Queue(maxsize=threads)

    for i in range(threads):
        t = threading.Thread(target=generate_random, args=(q, int(count/threads)))
        t.daemon = True
        t.start()

    count_inside = 0
    for _ in range(threads):
        count_inside += q.get()

    print(4.0 * count_inside / count)


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
