---
title: python script practicepython ex5 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'practicepython ex5'


Modules used in program: 
* `import random`

## python practicepython ex5

Python example: practicepython ex5

```python
#!/usr/bin/python

import random

a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]
c = []

for n in a:
  for m in b:
    if n == m:
      c.append(n)

print(c)

d = []
e = []
f = []

random.seed()

i = random.randint(1,30)
for j in range(0,i):
  d.append(random.randint(1,101))

k = random.randint(1,30)
for l in range(0,k):
  e.append(random.randint(1,101))


for o in d:
  for p in e:
    if o == p:
      f.append(o)

print(f)


print([ x for x,y in zip([ random.randint(1,101) for r in range(0,random.randint(1,30)) ],[ random.randint(1,101) for r in range(0,random.randint(1,30)) ]) if x == y ])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
