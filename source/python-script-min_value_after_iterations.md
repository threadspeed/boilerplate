---
title: python script min value after iterations (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'min value after iterations'


Modules used in program: 
* `import random`

## python min value after iterations

Python example: min value after iterations

```python
import random

iterations = 10
maxium_number = 100

min_value = random.randint(0,maxium_number)

print("<<<<<<<<<<<<<< initial minvalue: {}".format(min_value))

for iteration in range(0,iterations):
    new_random_value = random.randint(0,maxium_number)
    #print(new_random_value)

    if new_random_value < min_value:
        min_value = new_random_value

print("Minimun value after {} iterations is: {}".format(iterations, min_value))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
