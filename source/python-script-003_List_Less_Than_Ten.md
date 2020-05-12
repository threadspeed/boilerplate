---
title: python script 003 List Less Than Ten (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '003 List Less Than Ten'


## python 003 List Less Than Ten

Python mysql example: 003 List Less Than Ten

```python
# Exercise

# Take a list, say for example this one:

# a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
# and write a program that prints out all the elements of the list that are less than 5.

# Extras:

# 1. Instead of printing the elements one by one, make a new list that has
# all the elements less than 5 from this list in it and print(out this new list.)

# 2. Write this in one line of Python.

# 3. Ask the user for a number and return a list that contains only
# elements from the original list (a) that are smaller than that number given by the user.

a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
ls = []
for i in a:
    if i < 5:
        print(i, end=" ")
        ls.append(i) # Extras 1
print("\n")
print(ls)
print("\n")

# Extras 2

ls = [i for i in a if i < 5]

print("LC : ", ls)

# Extras 3
less = []
num = int(input("Give me a number."))
new = []
for i in a:
    if i < num:
        less.append(i)
print(less)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
