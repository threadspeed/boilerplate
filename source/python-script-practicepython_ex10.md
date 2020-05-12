---
title: python script practicepython ex10 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'practicepython ex10'


Modules used in program: 
* `import itertools`
* `import random`

## python practicepython ex10

Python mysql example: practicepython ex10

```python
#!/usr/bin/python

import random
import itertools

a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
b = [1, 2, 3, 4, 5, 5, 6, 7, 8, 9, 10, 11, 12, 13]

print(list(set([ x for x,y in list(itertools.product(a,b)) if x == y ])))

print(list(set([ x for x,y in list(itertools.product([ random.randint(1,101) for r in range(0,12) ],[ random.randint(1,101) for r in range(0,10) ])) if x == y ])))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
