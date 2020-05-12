---
title: python script LIST MERGE (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'LIST MERGE'


Modules used in program: 
* `import random`

## python LIST MERGE

Python example: LIST MERGE

```python
# To List Out the Common Unique Elements from Two Lists
# THE PROGRAM WILL GENERATE TWO LIST OF 12,16 ELEMENTS FROM A RANDOM SAMPLE OF 100 NUMBERS
# AND THEN IT WILL MERGE THE TWO LISTS INTO A NEW LIST
# THE NEW LIST WILL CONTAINS THE ELEMENTS THAT ARE UNIQUE TO BOTH THE LISTS
# TRY AND RUN THE PROGRAM , ITS PRETTY COOL.
import random
First=random.sample(range(100),12)
Second=random.sample(range(100),16)
Third=[n for n in set(First) if n in Second]
print("The First List Contains :",First)
print("The Second List Contains :",Second)
print("The New Generated list is :",Third)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
