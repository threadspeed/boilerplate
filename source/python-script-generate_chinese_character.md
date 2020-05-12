---
title: python script generate chinese character (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'generate chinese character'

Functions in program: 
* `def GB2312():`

Modules used in program: 
* `import random, string`

## python generate chinese character

Python example: generate chinese character

```python
import random, string
def GB2312():
    head = random.randint(0x4E00, 0x9FA5)
    return head

s=''
for i in range(1000):
    s=s+chr(GB2312())
    print(s)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
