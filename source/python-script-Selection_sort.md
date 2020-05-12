---
title: python script Selection sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Selection sort'

Functions in program: 
* `def selSort(nums):`

Modules used in program: 
* `import random`
* `import time`

## python Selection sort

Python mysql example: Selection sort

```python
import time
import random
random_items100 = [random.randint(1,10001) for c in range(100)]
random_items500 = [random.randint(1,10001) for c in range(500)]
random_items1000 = [random.randint(1,10001) for c in range(1000)]

def selSort(nums):
    n = len(nums)
    for bottom in range(n-1):
        mp = bottom
        for i in range(bottom+1, n):
            if nums[i] < nums[mp]:
                mp = i
        nums[bottom], nums[mp] = nums[mp], nums[bottom]

##Selection sort 성능 테스트(n=100)
startTime = time.clock()
selSort(random_items100)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for Selection_sort  is:', elapsedTime)

##Selection sort 성능 테스트(n=500)
startTime = time.clock()
selSort(random_items500)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for Selection_sort  is:', elapsedTime)

##Selection sort 성능 테스트(n=1000)
startTime = time.clock()
selSort(random_items1000)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for Selection_sort  is:', elapsedTime)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
