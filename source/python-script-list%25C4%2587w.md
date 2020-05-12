---
title: python script list%25C4%2587w (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'list%25C4%2587w'


Modules used in program: 
* `import timeit`
* `import random`
* `import random`

## python list%25C4%2587w

Python mysql example: list%25C4%2587w

```python
# numbList = []
# numbList.append(10)
# print(numbList)
# numbList=[1,2,3,4,5,6,7,8,9,10,1,1,1,1]
# print(numbList)
# print(numbList.count(1))
# print(numbList.extend(1))


# name = input('podaj imie : ')
# age = input('podaj wiek :')
# copies = input('how many copies:')
# copies = int(copies)
#
# print(('twoje imie: ' + name  +' twoj wiek : '+ age+'\n')*copies)



# num= input('give number: ')
# try:
#     num = int(num)
#     if num % 2 == 0:
#         print('number ' + str(num) + ' you give is even')
#     elif num % 2 != 0:
#         print('number' + str(num) + ' you give is not even')
# except ValueError:
#     print('the value ypu give is not a number')


# a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
# newList= []
# numb= input('Give number : ')
# newlist = []
#
# try:
#     numb = int(numb)
#     [newlist.append(x) for x in a if x < numb]
#     print(newlist)
# except ValueError:
#     print('this is not a number')

# for i in a:
#     if i < 5:
#         newList.append(i)
# print(newList)



# numb = input('give number: ')
# divList= []
# try:
#     numb = int(numb)
#     for i in range(2,numb+1):
#         if numb % i == 0:
#             divList.append(i)
#     print(divList)
# except ValueError:
#     print('bad input')
from string import digits

newList=[]
firstList = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
secondList = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]

import random
firstList.extend(secondList)
newList = list(set(firstList))
newList.sort()
print(newList)
import random
import timeit

# Random lists from [0-999] interval
randomList = [random.randint(0, 100) for r in range(10)]
randomList.sort()
newList.extend(randomList)
randomList=list(set(newList))
print(randomList)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
