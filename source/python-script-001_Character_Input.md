---
title: python script 001 Character Input (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '001 Character Input'


Modules used in program: 
* `import datetime`

## python 001 Character Input

Python mysql example: 001 Character Input

```python
# Exercise (and Solution)

# Create a program that asks the user to enter their name and their age.
# Print out a message addressed to them that tells them the year that they will turn 100 years old.


import datetime

name = input("Give me your name.\n")
age = int(input("Give me your age.\n"))

now = datetime.datetime.now()

year = (now.year - age) + 101  # If someone was born in 2000 he will be 1 year old in 2001.

print("{} will be 100 years old in the year {}.".format(name, year))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
