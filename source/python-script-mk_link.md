---
title: python script mk link (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mk link'


Modules used in program: 
* `import random`

## python mk link

Python mysql example: mk link

```python
#! /usr/bin/env python
import random

people_num = 10
links_loop = 15
upper="ABCDEFGHIJKLMNOPQRSTUVWXYZ"
lower="abcdefghijklmnopqrstuvwxyz"

a = 50
b = 450
people = [(random.choice(upper)
           +random.choice(lower)
           +random.choice(lower)
           +random.choice(lower),
           (random.randint(a,b),random.randint(a,b)))
          for x in range(people_num)]
print("people =", people)


linkset = set([(random.choice(people)[0],random.choice(people)[0])
               for i in range(links_loop)])
new_linkset = [x for x in linkset if len(set(x))!=1]
print("links =",)
print(new_linkset)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
