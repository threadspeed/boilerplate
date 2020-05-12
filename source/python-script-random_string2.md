---
title: python script random string2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random string2'

Functions in program: 
* `def random_string(length):`

Modules used in program: 
* `import random`
* `import array`

## python random string2

Python example: random string2

```python
import array
import random

def random_string(length):
    cs = array.array('B')
    for _ in xrange(length):
        cs.append(random.randrange(0x21, 0x7f))
    return cs.tostring()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
