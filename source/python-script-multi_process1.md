---
title: python script multi process1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multi process1'

Functions in program: 
* `def worker(num):`

Modules used in program: 
* `import time`
* `import random`
* `import multiprocessing`

## python multi process1

Python mysql example: multi process1

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-
import multiprocessing
import random
import time

def worker(num):
    for i in range(5):
    	print("{0},  {1}".format(num, i))
    return

if __name__ == '__main__':
    jobs = []
    for i in range(5):
        p = multiprocessing.Process(target=worker, args=(i,))
        jobs.append(p)
        p.start()

    # Iterate through the list of jobs and remove one that are finished, checking every second.
    for job in jobs:
    	job.join()

    print('*** All jobs finished ***')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
