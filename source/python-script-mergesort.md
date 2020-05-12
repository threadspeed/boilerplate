---
title: python script mergesort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mergesort'

Functions in program: 
* `def mergesort(list):`

Modules used in program: 
* `import random`

## python mergesort

Python mysql example: mergesort

```python
import random
from merge import merge

def mergesort(list):
    sortedness = 1

    while sortedness < len(list):
        for i in range(0, len(list), 2*sortedness):
            list1 = list[i:i+sortedness]
            list2 = list[i+sortedness:i+2*sortedness]
            list3 = merge(list1, list2)
            list[i:i+len(list3)] = list3
        sortedness = 2 * sortedness

    return list

if __name__ == '__main__':
    a = [random.randint(0, 100) for i in range(10)]
    print(a)
    print(mergesort(a))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
