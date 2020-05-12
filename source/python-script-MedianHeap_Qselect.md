---
title: python script MedianHeap Qselect (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MedianHeap Qselect'

Functions in program: 
* `def qselect(lst, k):`
* `def add_to_median_heap(minh, maxh, elem):`
* `def median(minh, maxh):`
* `def buildmax(lst): #make the initial maxheap`
* `def maxheapify(lst,n,i):`
* `def swap(lst,i,j):`

Modules used in program: 
* `import random`
* `import random`
* `import heapq`

## python MedianHeap Qselect

Python example: MedianHeap Qselect

```python
import heapq
import random
def swap(lst,i,j):
    lst[i],lst[j] = lst[j],lst[i]

def maxheapify(lst,n,i):
    root = i   # initialize root
    left = 2*i + 1  #define left child
    right = 2*i + 2  #define right child
    if left < n and lst[root] < lst[left]: #if the left child is bigger than root, switch
        root = left
    if right < n and lst[root] < lst[right]: #if the right child is bigger than root, switch
        root = right
    if root != i:  #if either of the previous two if statements are executed, make sure the indices align with the item
        swap(lst,i,root)
        maxheapify(lst,n,root)

def buildmax(lst): #make the initial maxheap
    n = len(lst)
    for i in range(n,-1,-1):
        maxheapify(lst,n,i)

sho = [int(100*(random.random())) for i in range(100)]

def median(minh, maxh):
    if len(minh) == 0 and len(maxh) == 0:
        m = "temp"
    elif len(minh) < len(maxh):
        m = maxh[0]
    elif len(maxh) < len(minh):
        m = minh[0]
    else:
        m = (maxh[0] + minh[0])/2
    return m

def add_to_median_heap(minh, maxh, elem):
    m = median(minh, maxh)
    if m == "temp":
        maxh.append(elem)
    else:
        if elem < m:
            maxh.append(elem)
            buildmax(maxh)
        elif elem > m:
            minh.append(elem)
            heapq.heapify(minh)
        else:
            minh.append(elem)
            heapq.heapify(minh)
    if abs(len(maxh)-len(minh)) > 1:
        if len(maxh) > len(minh):
            a = maxh[0]
            minh.append(a)
            maxh.remove(a)
            heapq.heapify(minh)
            buildmax(maxh)
        else:
            a = minh[0]
            maxh.append(a)
            minh.remove(a)
            heapq.heapify(minh)
            buildmax(maxh)

minh = []
maxh = []
for a in range(1,100,2):
    add_to_median_heap(minh, maxh, a)
print(median(minh, maxh))





######QSELECT######

def qselect(lst, k):
    min = []
    max = []
    for i in range(len(lst)):
        add_to_median_heap(min, max, lst[i])
    index = k-1
    while len(max) != k-1:
        if index < len(max):
            a = max[0]
            min.append(a)
            max.remove(a)
            heapq.heapify(min)
            buildmax(max)
        if len(max) < index:
            a = min[0]
            max.append(a)
            min.remove(a)
            heapq.heapify(min)
            buildmax(max)
    return min[0]

import random
random.seed(123)
lst = [i for i in range(1000)]
random.shuffle(lst)
for a in range(1000):
    print(qselect(lst, a+1))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
