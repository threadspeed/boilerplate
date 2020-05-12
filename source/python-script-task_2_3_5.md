---
title: python script task 2 3 5 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'task 2 3 5'

Functions in program: 
* `def str2(length):`

Modules used in program: 
* `import random, string`

## python task 2 3 5

Python example: task 2 3 5

```python
# Дана строка.
# Если ее длина больше 10, то оставить в строке только первые 6 символов,
# иначе дополнить строку символами 'o' до длины 12.
#
# import random, string
#
# def str1(size = 20, chars=string.ascii_uppercase + string.digits):
#     return ''.join(random.choice(chars) for _ in range(size)) #
#     # не понял как сделать строку с случайным количеством символов, но не <20 и >8
#
# print(str1())

import random, string

def str2(length):
   letters = string.ascii_lowercase
   return ''.join(random.choice(letters) for i in range(length))
print(str2(20))

str3 = str2(20)
print(str3)

if len(str3) >= 10:
    str4 = str3[0:6]
    print(str4)

i = 0
while i < 6:
    str4 = str4 + '0'
    i += 1
print('Solution:',str4)

print(len(str4))



l = str4
i = 0
for i in range(12):
    # l.zfill('o')
    i += 1
    s = ''.join(l)
print(s)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
