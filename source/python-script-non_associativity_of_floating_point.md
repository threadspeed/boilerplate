---
title: python script non associativity of floating point (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'non associativity of floating point'


Modules used in program: 
* `import random`

## python non associativity of floating point

Python mysql example: non associativity of floating point

```python
import random
from random import random, seed
# reduce import for Python 3.x support
# (also works in Python 2.x but is redundant)
from functools import reduce

seed(42)

data = [random() for i in range(1000000)]
sum = lambda x: reduce(lambda y, z: y + z, x)
print("%.16f" % (sum(data) - sum(reversed(data))))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
