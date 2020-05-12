---
title: python script Password generator script (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Password generator script'

Functions in program: 
* `def generate_pwd(length, slvl):`

Modules used in program: 
* `import random`
* `import string`

## python Password generator script

Python mysql example: Password generator script

```python
import string
import random
from random_word import RandomWords
rw = RandomWords()

def generate_pwd(length, slvl):
    if slvl == 1:
        pwd = rw.get_random_word(minLength=length)
    elif slvl == 2:
        temp = string.ascii_letters + string.digits
        pwd = ''.join(random.choice(temp) for i in range(length))
    elif slvl == 3:
        temp = string.ascii_letters + string.digits + string.punctuation
        pwd = ''.join(random.choice(temp) for i in range(length))
    else:
        exit('Invalid input given for strength')
    return pwd

print('''Choose Strength of your password:
1 : Weak
2 : Medium
3 : Strong :''')
slvl = int(input())
length = int(input('Enter length of password: '))
if length > 15 or length < 6:
    length = random.randint(6, 15)
    print('\nLength is either too short or larger than 15\nHence using random value: ',length)
else:
    pass

print('Genrated password : '+ generate_pwd(length, slvl))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
