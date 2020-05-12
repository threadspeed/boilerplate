---
title: python script random string (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random string'

Functions in program: 
* `def random_string(length):`

Modules used in program: 
* `import random`

## python random string

Python example: random string

```python
import random

def random_string(length):
    return ''.join([ chr(random.randrange(0x21, 0x7f)) for _ in xrange(length) ])

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
