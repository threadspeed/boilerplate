---
title: python script Count(selection sort) (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Count(selection sort)'

Functions in program: 
* `def selSort(nums):`

Modules used in program: 
* `import random`
* `import time`

## python Count(selection sort)

Python example: Count(selection sort)

```python
import time
import random
random_items100 = [random.randint(1,10001) for c in range(100)]
random_items500 = [random.randint(1,10001) for c in range(500)]
random_items1000 = [random.randint(1,10001) for c in range(1000)]

def selSort(nums):
    selcount = 0
    n = len(nums)
    for bottom in range(n-1):
        mp = bottom
        for i in range(bottom+1, n):
            selcount +=1
            if nums[mp] > nums[i]:
                mp = i
        nums[bottom], nums[mp] = nums[mp], nums[bottom]
    print(selcount)
    
selSort(random_items100)
selSort(random_items500)
selSort(random_items1000)
selSort([8,7,6])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
