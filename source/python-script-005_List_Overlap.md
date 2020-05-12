---
title: python script 005 List Overlap (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '005 List Overlap'


Modules used in program: 
* `import random`

## python 005 List Overlap

Python mysql example: 005 List Overlap

```python
# Exercise

# Take two lists, say for example these two:

# a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
# b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]

# and write a program that returns a list that contains only
# the elements that are common between the lists (without duplicates).
# Make sure your program works on two lists of different sizes.

# Extras:

# 1. Randomly generate two lists to test this
# Write this in one line of Python (don’t worry if you can’t figure this out at this point - we’ll get to it soon)

import random

a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]

ls = []

for i in b:
    if i in a:
        ls.append(i)
print(ls)

x = [i for i in b if i in a] # Extras - List Comprehension
print("List Comprehension:", x)
print("")
# Extras
ranA = []
ranB = []
ranC = []
i = 1
while i <= 10:
    r = random.randint(1, 50)
    ra = random.randint(30, 50)
    ranA.append(r)
    ranB.append(ra)
    i += 1
for i in ranB:
    if i in ranA:
        ranC.append(i)
print("Random List A:", ranA)
print("Random List B:", ranB)
print(ranC)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
