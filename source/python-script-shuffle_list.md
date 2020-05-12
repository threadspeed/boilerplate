---
title: python script shuffle list (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'shuffle list'


Modules used in program: 
* `import random`

## python shuffle list

Python mysql example: shuffle list

```python
import random

a = ['a', 'b', 'c']
b = [1, 2, 3]

c = list(zip(a, b))

random.shuffle(c)

a, b = zip(*c)

print(a)
print(b)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
