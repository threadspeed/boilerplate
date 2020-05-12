---
title: python script timingMinFunction (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'timingMinFunction'


Modules used in program: 
* `import random`
* `import timeit`

## python timingMinFunction

Python example: timingMinFunction

```python
import timeit
import random
lyst = random.sample(range(1,500000000), 100)
print(str(lyst))
dictionary = dict(x, lyst[x] for x in range(len(lyst)))
print(str(dictionary))
toople = tuple(lyst[x] for x in range(len(lyst)))
print(str(lyst))
print("list time is " + str(timeit.timeit(stmt = "3 in lyst")))
print("list dictionary is " + str(timeit.timeit(stmt = "3 in dictionary.keys")))
print("list tuple is " + str(timeit.timeit(stmt = "3 in toople")))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
