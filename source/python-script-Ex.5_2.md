---
title: python script Ex.5 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Ex.5 2'


Modules used in program: 
* `import random`
* `import random`
* `import random`

## python Ex.5 2

Python example: Ex.5 2

```python

# coding: utf-8

# From Practicepython.org
# 
# Solution by: Seung Jung Jin
# Date: June 30, 2016
# 
# Ex5)
# Take two lists, say for example these two:
# 
#   a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
#   b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]
# 
# and write a program that returns a list that contains only the elements that are common between the lists (without duplicates). Make sure your program works on two lists of different sizes.
# 
# Extras:
# 
#     Randomly generate two lists to test this
#     Write this in one line of Python (don’t worry if you can’t figure this out at this point - we’ll get to it soon)
# 



a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]
c = []

for i in range(0, len(a)):
    for j in range(0, len(b)):
        if a[i] in c:
            pass
        else:
            c.append(a[i])
            
c


# In[30]:

import random
a = [random.randrange(1, 10) for _ in range(0, random.randint(1,20))]
b = [random.randrange(1, 10) for _ in range(0, random.randint(1,20))]
c = []

for i in range(0, len(a)):
    for j in range(0, len(b)):
        if a[i] in c:
            pass
        else:
            if a[i] == b[j]:
                c.append(a[i])
            
print('list a:', a)
print('list b:', b)
print('list c:', c)



import random
a = [random.randrange(1, 10) for _ in range(0, random.randint(1,20))]
b = [random.randrange(1, 10) for _ in range(0, random.randint(1,20))]
c = []

for i in range(0, len(a)):
    if a[i] in b and a[i] not in c:
        c.append(a[i])
print(a)
print(b)
print(c)


import random
a = [random.randrange(1, 10) for _ in range(0, random.randint(1,20))]
b = [random.randrange(1, 10) for _ in range(0, random.randint(1,20))]
c = []

# list comprehension; doens't exclude repeats
c = [a[i] for i in range(0, len(a)) if (a[i] not in c and a[i] in b)]
print(a)
print(b)
print(c)





```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
