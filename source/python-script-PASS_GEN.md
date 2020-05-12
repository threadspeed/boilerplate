---
title: python script PASS GEN (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PASS GEN'

Functions in program: 
* `def ps_gen(size=8,chars=string.ascii_letters + string.digits + string.punctuation):`

Modules used in program: 
* `import string`
* `import random`

## python PASS GEN

Python example: PASS GEN

```python
# PASSWORD GENERATOR
# THIS PROGRAM WILL HELP TO GENERATE PASSWORD OF YOUR LENGTH
# IT WILL TAKE THE LENGTH OF THE PASSWORD DESIRED BY THE USER.
# AND THEN FROM ITS SET OF ALPHABETS AND SPECIAL CHARACTERS IT WILL SUGGEST YOU A PASSWORD.
# QUITE USEFUL


import random
import string


def ps_gen(size=8,chars=string.ascii_letters + string.digits + string.punctuation):
    return " ".join(random.sample(chars, size))
# return " ".join(random.choice(chars) for _ in range(size))


size = int(input("Please Enter Strength Of Your Password i.e From 0-9 :"))
password = ps_gen(size)
print("Your Password Should Be:",password)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
