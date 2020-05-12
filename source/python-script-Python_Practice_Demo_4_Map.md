---
title: python script Python Practice Demo 4 Map (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Python Practice Demo 4 Map'


Modules used in program: 
* `import os`
* `import sys`
* `import random`

## python Python Practice Demo 4 Map

Python example: Python Practice Demo 4 Map

```python
import random
import sys
import os

food = {'drinks' : 'Cola',
        'snacks' : 'Chips',
        'desert' : 'Cake',
        'main food' : 'Noodle'}
print(food)
print(food['drinks'])

del food['drinks']
print(food)

food['desert'] = 'Chocolate'
print(food)
print(len(food))

print(food.get('desert'))

print(food.keys())
print(food.values())

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
