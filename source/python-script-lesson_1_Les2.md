---
title: python script lesson 1 Les2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'lesson 1 Les2'


Modules used in program: 
* `import math`
* `import random`

## python lesson 1 Les2

Python mysql example: lesson 1 Les2

```python
found_coins = 20
magic_coins = 70
stolen_coins = 3
coins = found_coins
# for week in range (1,53):
# coins = coins + magic_coins - stolen_coins
# print('Неделя %s = %s' % (week, coins))


import random
import math

x = random.randint(0, 200)
y = random.randint(50, 400)
while x < 200 and y < 400:
    x = int(x + (x / 2))
    y = int(y + (y / 2))
    print(x, y)

print('another code')
k = random.randint(40,105)
print(k)
k = k + (k/ 2)
print(k)
k = int(round(k))
print(k)



for x in range(0, 20):
    print('привет %s' % x)
    if x < 20:
        break


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
