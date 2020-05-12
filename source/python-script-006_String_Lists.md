---
title: python script 006 String Lists (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '006 String Lists'


Modules used in program: 
* `import random`

## python 006 String Lists

Python mysql example: 006 String Lists

```python
# Exercise

# Ask the user for a string and print(out whether this string is a palindrome or not.)
# (A palindrome is a string that reads the same forwards and backwards.)

string = input("Enter a string. I will find out the PALINDROME.\n")

import random
if string == string[::-1]:  # [::-1] reverse the string.
    print(">>>> It is palindrome.")
else:
    print(">>>> It is not palindrome.")


# List Indexing

r = range(0, 10)
ls = []
for i in r:
    i = random.randint(1, 10)
    ls.append(i)
print(ls)
print(ls[1:5:2])

# Strings are Lists

string = "samrat"
for i in string:
    print("Letter: ", i)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
