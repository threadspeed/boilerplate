---
title: python script listoverlap (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'listoverlap'


Modules used in program: 
* `import random`
* `import random`

## python listoverlap

Python mysql example: listoverlap

```python
#First version

import random
  
a = random.sample(range(20), 12)
b = random.sample(range(20), 15)

print(a)
print(b)

new = []
for i in a:
  if i in b:
    new.append(i)
    b.remove(i)
print(new)


#Second version (with list comprehension)

import random
  
a = random.sample(range(20), 12)
b = random.sample(range(20), 15)

print(a)
print(b)

print([i for i in a if i in b])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
