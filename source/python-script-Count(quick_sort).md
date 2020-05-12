---
title: python script Count(quick sort) (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Count(quick sort)'

Functions in program: 
* `def quick_sort(items):`

Modules used in program: 
* `import random`
* `import time`

## python Count(quick sort)

Python mysql example: Count(quick sort)

```python
#Quick Sort
import time
import random

random_items100 = [random.randint(1,10001) for c in range(100)]
random_items500 = [random.randint(1,10001) for c in range(500)]
random_items1000 = [random.randint(1,10001) for c in range(1000)]

quickcount = 0

def quick_sort(items):
    global quickcount
    if len(items) > 1:
        pivot_index = len(items) // 2 # 홀수이면 정중아에 있는 요소, 짝수이면 우측으로 한칸 치우친 위치
        smaller_items = []
        larger_items = []
        for i, val in enumerate(items): #i는 인덱스값, val은 요소값
            if i != pivot_index: # 인덱스 값 자신하고는 비교하는 경우를 제외하기 위해
                quickcount += 1
                if val < items[pivot_index]: #pivot 보다 작으면 smaller list에 넣기
                    smaller_items.append(val)
                else:                        #pivot 보다 크면 larger list에 넣기
                    larger_items.append(val)
        #smaller or larger는 items[pivot_index]보다 작거나 크기는 하지만
        #자기들끼리는 대소비교가 안이루어진 상태라 아래의 recursion 과정이 필요하다.
        quick_sort(smaller_items)
        quick_sort(larger_items)
        items[:] = smaller_items + [items[pivot_index]] + larger_items

#quick_sort(random_items100)
#quick_sort(random_items500)
quick_sort(random_items1000)
#quick_sort([6,5,3,2,1])
print(quickcount)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
