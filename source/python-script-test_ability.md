---
title: python script test ability (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test ability'


Modules used in program: 
* `import random`
* `import build_password`

## python test ability

Python mysql example: test ability

```python
import build_password
import random

names = ['amazon', 'ebay', 'facebook', 'golf', 'winter', 'chad', 'night', 'water', 'airforce', 'lauren', 'david', 'anne', 'theboohers']

while(True):
    name = names[random.randint(0, len(names) - 1)]
    input_answer = input(name + '? : ')
    answer = build_password.set_password(name)
    if input_answer == answer:
        print('yeah!')
    else:
        print('nope, it was ' + answer)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
