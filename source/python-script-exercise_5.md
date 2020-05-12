---
title: python script exercise 5 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exercise 5'


Modules used in program: 
* `import random`

## python exercise 5

Python mysql example: exercise 5

```python
#Exercise 5

#Take two lists,
#and write a program that returns a list that contains only the elements that are common between the lists (without duplicates). Make sure your program works on two lists of different sizes.

#Extras:
#1. Randomly generate two lists to test this
#2. Write this in one line of Python

#import random
import random

#create lists
a = random.sample(range(100),10)
b = random.sample(range(100),15)
c = []

#append element, which is overlapping in a & b, into c
c = [elem for elem in a if elem in b and elem not in c]

#print(lists)
print("List 1: " + str(a))
print("List 2: " + str(b))
print("List overlap: " + str(c))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
