---
title: python script reader (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'reader'

Functions in program: 
* `def read():`

Modules used in program: 
* `import tables`
* `import multiprocessing`
* `import random`

## python reader

Python example: reader

```python
# This crashes

import random
import multiprocessing

import tables

def read():
    for _ in range(100):
        h5.root.data.data_array[random.randint(0, int(1e6)-1)]

h5 = tables.open_file('onefile.h5')

read()  # It works!

# Stress-test
processes = [multiprocessing.Process(target=read) for _ in range(1000)]
for p in processes:
    p.start()
    
print('Joining')
for p in processes:
    p.join()

h5.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
