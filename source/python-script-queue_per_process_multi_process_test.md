---
title: python script queue per process multi process test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'queue per process multi process test'

Functions in program: 
* `def enqueue(_queue, count):`

Modules used in program: 
* `import random`
* `import time`
* `import sys`
* `import os`
* `import multiprocessing`

## python queue per process multi process test

Python mysql example: queue per process multi process test

```python
import multiprocessing
import os
import sys
import time
import random

def enqueue(_queue, count):
    _queue.cancel_join_thread()
    for i in range(count):
        _queue.put(random.randint(0,count), timeout=1)

queues = []
processes = []
concurrency = 24

s = time.time()
for i in range(concurrency):
    q = multiprocessing.Queue()
    queues.append(q)
e = time.time() - s
print(f'{e}')

start = time.time()
for i in range(concurrency):
    p = multiprocessing.Process(target=enqueue, args=[queues[i], 10000])
    p.start()
    processes.append(p)
    queues.append(q)

for p in processes:
    p.join()
elapsed_time = time.time() - start
print(f'{elapsed_time}')


for i in range(concurrency):
    print(queues[i].qsize())

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
