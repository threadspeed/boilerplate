---
title: python script random16byte 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random16byte 2'


Modules used in program: 
* `import random`

## python random16byte 2

Python example: random16byte 2

```python
import random

s = "0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz"
for i in range(16):
  x = random.randint(0, 10 + 26 + 26 - 1)
  print(s[x], end="")
print('')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
