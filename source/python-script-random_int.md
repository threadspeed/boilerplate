---
title: python script random int (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random int'


Modules used in program: 
* `import sys`
* `import random`

## python random int

Python example: random int

```python
# -*- coding:utf-8 -*-

import random
import sys

argvs = sys.argv
argc = len(argvs)

if (argc != 6):
  print('[Error]')
  print('  ex) python random_string.py [min_size] [max_size] [output_count] [prefix] [suffix]')
  quit()

# for i in range(argc):
#  print(argvs[i])

for loop in range(int(argvs[3])):
  print(argvs[4] + str(random.randint(int(argvs[1]), int(argvs[2])))  + argvs[5])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
