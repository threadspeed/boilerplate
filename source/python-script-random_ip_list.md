---
title: python script random ip list (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random ip list'

Functions in program: 
* `def generating_ips(int):`

Modules used in program: 
* `import random`

## python random ip list

Python mysql example: random ip list

```python
import random
def generating_ips(int):
    ips =[]
    for x in range(0,int):
        ip = '{}.{}.{}.{}'.format(*__import__('random').sample(range(0, 255), 4))
        ips.append(ip) 
        
    return ips

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
