---
title: python script fyzzer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'fyzzer'


Modules used in program: 
* `import random,gdb`

## python fyzzer

Python example: fyzzer

```python
import random,gdb

g=gdb.gdb()

msgs=[]
msgs+=['p','P','s','z','Z','q','m','M','e']
msgs+=['P0:','M0:']

for msg in msgs:
    for i in range(1,100):
        g.send(msg+'A'*i*50)
        print('{}*{}'.format(msg,50*i))
        g.recv_msg()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
