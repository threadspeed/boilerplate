---
title: python script insertion sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'insertion sort'

Functions in program: 
* `def insertion_sort(items):`

Modules used in program: 
* `import random`
* `import time`

## python insertion sort

Python example: insertion sort

```python
import time
import random
random_items100 = [random.randint(1,10001) for c in range(100)]
random_items500 = [random.randint(1,10001) for c in range(500)]
random_items1000 = [random.randint(1,10001) for c in range(1000)]

def insertion_sort(items):
    for i in range(1, len(items)):
        j = i
        while j > 0 and items[j-1] > items[j]:
            items[j], items[j-1] = items[j-1], items[j]
            j -= 1 #여기서 j가 작아지면서 while문을 계속 돌릴것인지 판단한다
    return(items)

####insertion_sort 성능 테스트(n=100)
startTime = time.clock()
insertion_sort(random_items100)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for insertion_sort  is:', elapsedTime)

##insertion_sort 성능 테스트(n=500)
startTime = time.clock()
insertion_sort(random_items500)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for insertion_sort  is:', elapsedTime)

##insertion_sort 성능 테스트(n=1000)
startTime = time.clock()
insertion_sort(random_items1000)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for insertion_sort  is:', elapsedTime)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
