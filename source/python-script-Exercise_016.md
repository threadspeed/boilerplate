---
title: python script Exercise 016 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Exercise 016'


Modules used in program: 
* `import random`

## python Exercise 016

Python mysql example: Exercise 016

```python
#Import random module
import random
#Possible characters
lett = "abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ01234567890!@#$%^&*()?"
#Get length from user
length = int(input("How many characters should your password be? "))
#Generate from possibles
paswd = "".join(random.sample(lett,length ))
print(paswd)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
