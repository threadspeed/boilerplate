---
title: python script random access (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random access'

Functions in program: 
* `def random_read(str):`

Modules used in program: 
* `import random`
* `import time`
* `import os`
* `import mmap`

## python random access

Python example: random access

```python
import mmap
import os
import time
import random

def random_read(str):
    with open(str, "r+b") as f:
        mm = mmap.mmap(f.fileno(), 0)
        fsize = os.fstat(f.fileno()).st_size
        list = range(fsize)
        start = time.time()
        for i in list:
            j=mm[list[i]]
        seq = time.time()-start
        random.shuffle(list)

        start = time.time()
        for i in list:
            j=mm[list[i]]
        rnd = time.time() - start

        print("%d \t %.20f \t %.20f" % (fsize, seq, rnd))

random_read("data")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
