---
title: python script Bubble sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Bubble sort'

Functions in program: 
* `def bubble_sort(items):`

Modules used in program: 
* `import random`
* `import time`

## python Bubble sort

Python mysql example: Bubble sort

```python
import time
import random
random_items100 = [random.randint(1,10001) for c in range(100)]
random_items500 = [random.randint(1,10001) for c in range(500)]
random_items1000 = [random.randint(1,10001) for c in range(1000)]

#bubbl_sort : 맨앞에서부터 인접한 두개의 요소들을 차례로 비교하여, 제일 큰 값은 맨 뒤에 위치시키는 함수
#매 단계를 거듭할수록 제일 끝자리부터 맨앞자리까지 그자리에 위치할 값을 확정한다.
def bubble_sort(items):
    for i in range(len(items)): # i=0일때, 맨 뒤자리에 위치할 요소 찾을 수 있음.
    #i=1일땐 그 앞자리.....i=len(items)-1일땐 두번째 자리 위치할 요소 찾을 수 있음(마지막으로 맨앞은 자동)
        for j in range(len(items)-1-i): # 밑에 j+1이 있으니깐 len(items)-1-i해야
            if items[j] > items[j+1]: # 인접한 요소 둘 중에서 왼쪽에 있는 요소가 오른쪽에 있는 경우
                items[j], items[j+1] = items[j+1], items[j] # 자리를 바꿔준다.

####bubble_sort 성능 테스트(n=100)
startTime = time.clock()
bubble_sort(random_items100)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for bubble_sort     is:', elapsedTime)

##bubble_sort 성능 테스트(n=500)
startTime = time.clock()
bubble_sort(random_items500)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for bubble_sort     is:', elapsedTime)

##bubble_sort 성능 테스트(n=1000)
startTime = time.clock()
bubble_sort(random_items1000)
endTime = time.clock()
elapsedTime = endTime - startTime
print('The elapsed time for bubble_sort     is:', elapsedTime)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
