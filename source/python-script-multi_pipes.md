---
title: python script multi pipes (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multi pipes'

Functions in program: 
* `def main():`
* `def f(count, chan):`

Modules used in program: 
* `import random`

## python multi pipes

Python mysql example: multi pipes

```python
from multiprocessing import Process, Pipe
import random


def f(count, chan):
    output = []
    for i in xrange(count):
        output.append(random.randint(0, 10))
    chan.send(output)


def main():
    s = 1000000
    count = 2
    forproc = s/2
    jobs = []
    parent_ends = []
    for i in xrange(count):
        parent_end, child_end = Pipe()
        p = Process(target=f, args=(forproc, child_end))
        p.start()
        jobs.append(p)
        parent_ends.append(parent_end)

    result = []
    for end in parent_ends:
        value = end.recv()
        result.extend(value)

    for job in jobs:
        job.join()

    print(len(result))


if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
