---
title: python script Generator891 ABC (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Generator891 ABC'

Functions in program: 
* `def run():`
* `def createData(num):`

Modules used in program: 
* `import random`
* `import time`
* `import os`

## python Generator891 ABC

Python example: Generator891 ABC

```python
import os
import time
import random

def createData(num):
    for i in range(num):
        randdata = []
        for _ in range(3):
            randdata.append(random.randint(1, 10 ** 4 + 1))
        randdata.sort()
        print(" ".join([str(i) for i in randdata]))

def run():
    createData(10)

if __name__ == "__main__":
    print("start!")
    run()
    print("end!")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
