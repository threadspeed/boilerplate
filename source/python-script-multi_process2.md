---
title: python script multi process2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'multi process2'

Functions in program: 
* `def worker(num):`

Modules used in program: 
* `import random, time`

## python multi process2

Python mysql example: multi process2

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-
from multiprocessing import Pool
import random, time

def worker(num):
    for i in range(5):
    	print("{0},  {1}".format(num, i))
    return

if __name__ == '__main__':
    
    pool = Pool(processes=4)
    pool.map(worker, range(5))

    print('*** All jobs finished ***')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
