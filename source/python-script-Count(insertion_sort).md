---
title: python script Count(insertion sort) (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Count(insertion sort)'

Functions in program: 
* `def insertion_sort(items):`

Modules used in program: 
* `import random`
* `import time`

## python Count(insertion sort)

Python example: Count(insertion sort)

```python
import time
import random
random_items100 = [random.randint(1,10001) for c in range(100)]
random_items500 = [random.randint(1,10001) for c in range(500)]
random_items1000 = [random.randint(1,10001) for c in range(1000)]

def insertion_sort(items):
    count = 0
    for i in range(1, len(items)):
        j = i
        #while j > 0 and items[j-1] > items[j]: while문을 아래와 같이 바꾸었음.
        if j > 0:
            for a in range(j,0,-1):
                count += 1
                if items[a-1] > items[a]:
                    items[a], items[a-1] = items[a-1], items[a]
                else: break
    print(count) #insertion의 정확한 갯수는

insertion_sort(random_items100)
insertion_sort(random_items500)
insertion_sort(random_items1000)
insertion_sort([2,4,5])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
