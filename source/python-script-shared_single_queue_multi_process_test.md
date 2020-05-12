---
title: python script shared single queue multi process test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'shared single queue multi process test'

Functions in program: 
* `def enqueue(count):`

Modules used in program: 
* `import random`
* `import time`
* `import sys`
* `import os`
* `import multiprocessing`

## python shared single queue multi process test

Python mysql example: shared single queue multi process test

```python
import multiprocessing
import os
import sys
import time
import random

def enqueue(count):
    test_queue.cancel_join_thread()
    for i in range(count):
        test_queue.put(random.randint(0,count), timeout=1)

test_queue = multiprocessing.Queue()
processes = []
concurrency = 24

start = time.time()
for i in range(concurrency):
    p = multiprocessing.Process(target=enqueue, args=[10000])
    p.start()
    processes.append(p)

for p in processes:
    p.join()
elapsed_time = time.time() - start
print(f'{elapsed_time}')

print(test_queue.qsize())

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
