---
title: python script list overlap comprehensions (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'list overlap comprehensions'


Modules used in program: 
* `import random`

## python list overlap comprehensions

Python mysql example: list overlap comprehensions

```python
import random
a = random.sample(range(1, 30), 16)
b = random.sample(range(1, 30), 12)
print(a)
print(b)
common = [x for x in a and b if x in a and x in b]
print(common)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
