---
title: python script List%2520Overlap%2520Comprehensions (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'List%2520Overlap%2520Comprehensions'

Functions in program: 
* `def merge_list(list_1, list_2) :`

Modules used in program: 
* `import random`
* `import random`

## python List%2520Overlap%2520Comprehensions

Python example: List%2520Overlap%2520Comprehensions

```python
import random
def merge_list(list_1, list_2) :
    list_1 = list(set(list_1))
    list_2 = list(set(list_2))
    #merged_list = [i for i in list_1 for j in list_2 if i==j]
    merged_list = [i for i in list_1 if i in  list_2]
    return merged_list
import random
list_1 = random.sample(range(10,20),8)
list_2  = random.sample(range(10,20),6)
print(merge_list(list_1,list_2))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
