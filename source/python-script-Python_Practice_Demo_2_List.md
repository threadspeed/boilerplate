---
title: python script Python Practice Demo 2 List (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Python Practice Demo 2 List'


Modules used in program: 
* `import os`
* `import sys`
* `import random`

## python Python Practice Demo 2 List

Python mysql example: Python Practice Demo 2 List

```python
import random
import sys
import os

fruit_list = ['apple',
              'banana',
              'peach',
              'lemon',
              'watermelon'
              ]

print('First Item', fruit_list[0])  #[0] - is the first
print(fruit_list)
print(fruit_list[2:5])  #[2:5] - 2 is the 3rd one on the list, 5 is the the fifth thing on the list; [2:5] means start from the 3rd one until to the 5th one on the list

event_list = ['wash car', 'pick up kids','cash check']

to_do_list = [fruit_list, event_list]
print(to_do_list)
print(to_do_list[1][1])

fruit_list.append('blueberry')  # list.append() to add a new item to the list
print(to_do_list)

fruit_list.insert(2, 'woman')
print(fruit_list)

fruit_list.remove('woman')
print(fruit_list)

fruit_list.sort()   # .sort() - to sort the items on the list
print(fruit_list)

fruit_list.reverse()    #.reverse() - to sort the items on the list in negative way
print(fruit_list)

del fruit_list[4]   # del - is similar with list.remove
print(fruit_list)

to_do_list2 = fruit_list + event_list
print(to_do_list2)

print(len(to_do_list))
print(len(to_do_list2))
print(max(to_do_list2))
print(min(to_do_list2))

to_do_list2.append('aab')
print(to_do_list2)
print(max(to_do_list2))
print(min(to_do_list2))
# max() and min() is not about the length of the item




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
