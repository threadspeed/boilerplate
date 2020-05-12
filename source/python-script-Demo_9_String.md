---
title: python script Demo 9 String (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Demo 9 String'


Modules used in program: 
* `import os`
* `import sys`
* `import random`

## python Demo 9 String

Python example: Demo 9 String

```python
import random
import sys
import os


long_string = "  i'll catch you if you fall - The Floor "

print(long_string[2:6])
print(long_string[-7:])
print(long_string[:-7])

print("%c is my %s letter and my number %d number is %.5f" %
      ("R", "Favorate", 3, 0.123128))

print(long_string.capitalize())
print(long_string.find("Floor"))
print(long_string.isalpha()) #.isalpha is to check whether the string just consists of alphabetic character only.
print(long_string.isalnum()) #.isalnum is to check whether the string just consists of number only
print(len(long_string))
print(long_string.replace("Floor","Ground"))
print(long_string.strip()) #.strip is to clean the whitespace initiate and end of the string

quote_list = long_string.split(" ")
print(quote_list)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
