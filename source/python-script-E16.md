---
title: python script E16 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'E16'

Functions in program: 
* `def pasgen(leng):`

Modules used in program: 
* `import random`

## python E16

Python mysql example: E16

```python
import random
print(("                    << Random Password Maker >>"))
letter = "QWERTYUIOPASDFGHJKLZXCVBNM1234567890abcdefghijklmnopqrstuvwxyz1234567890!@#$%^&*()_+"

def pasgen(leng):
    pas= ''.join(random.sample(letter,leng))
    return pas

while 1 == 1:
    print((pasgen(int(input("Length of desired password? : ")))))
    
### using internals of python
##import string
##import random
##
##def pw_gen(size = 8, chars=string.ascii_letters + string.digits + string.punctuation):
##	return ''.join(random.choice(chars) for _ in range(size))
##
##print(pw_gen(int(input('How many characters in your password?'))))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
