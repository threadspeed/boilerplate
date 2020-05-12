---
title: python script random16byte (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random16byte'


Modules used in program: 
* `import random`

## python random16byte

Python example: random16byte

```python
import random

for i in range(16):
  x = random.randint(0, 10 + 26 + 26 - 1)
  if x < 10:
    a = chr(ord('0') + x)
  elif x >= 10 and x < 10 + 26:
    a = chr(ord('A') + x - 10)
  else:
    a = chr(ord('a') + x - 10 - 26)
  print(a, end="")
print('')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
