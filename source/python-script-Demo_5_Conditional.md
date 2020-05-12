---
title: python script Demo 5 Conditional (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Demo 5 Conditional'


Modules used in program: 
* `import os`
* `import sys`
* `import random`

## python Demo 5 Conditional

Python example: Demo 5 Conditional

```python
import random
import sys
import os

age = 27

if age > 16:
    print('you are old enough to drive')
else:
    print('You are not old enough to drive')

if age >= 21:
    print('You are old enough to drive a tractor trailer')
elif age >= 16:
    print('You are old enough to drive a car')
else:
    print('You are not old enough to drive')

if ((age>=1) and (age <=18)):
    print('You get a birthday')
elif (age == 21) or (age >= 65):
    print('You get a birthday')
elif not (age == 30):
    print("You don't get a birthday")
else:
    print("You get a birthday party yeah")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
