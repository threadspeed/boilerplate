---
title: python script Demo 7 WhileLoop (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Demo 7 WhileLoop'


Modules used in program: 
* `import os`
* `import sys`
* `import random`

## python Demo 7 WhileLoop

Python mysql example: Demo 7 WhileLoop

```python
import random
import sys
import os

random_num = random.randrange(0,100)
account_num = 0
while(random_num != 15):
    account_num += 1
    print(account_num,'.', random_num)
    random_num = random.randrange(0,100)

print('\n')

print('''Find the odd number in between 0 and 20,
finish the loop once up to 9
''')

i = 0

while( i <= 20):
    if( i % 2 == 0):
        print(i)
    elif(i == 9):
        break
    else:
        i += 1
        continue
    i += 1

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
