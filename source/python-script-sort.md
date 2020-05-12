---
title: python script sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sort'

Functions in program: 
* `def test_quick_sort_inplace():`
* `def quick_sort2(alist: list, beg: int, end: int):`
* `def partition2(alist, beg, end):`
* `def quick_sort_inplace(alist, beg, end):`
* `def partition(alist, beg, end):`
* `def quick_sort(alist):`
* `def mergeing(list1, list2):`
* `def merge_sort(alist):`
* `def shell_sort(alist):`
* `def insert_sort(alist):`
* `def select_sort(alist):`
* `def bububle_sort2(alist):`
* `def bububle_sort(alist):`

## python sort

Python example: sort

```python
def bububle_sort(alist):
    n = len(alist)
    for j in range(n-1):
        count = 0
        for i in range(n-1-j):
            if alist[i] > alist[i+1]:
                alist[i+1], alist[i] = alist[i], alist[i+1]
                count += 1
        if count == 0:
            return alist
    return alist

def bububle_sort2(alist):
    n = len(alist)
    for i in range(n-1):
        for j in range(i+1, n):
            if alist[i] > alist[j]:
                alist[i], alist[j] = alist[j], alist[i]
    return alist


def select_sort(alist):
    n = len(alist)
    for i in range(n-1):
        min_index = i
        for j in range(i+1, n):
            if alist[j] < alist[min_index]:
                min_index = j
        if min_index != i:
            alist[i], alist[min_index] = alist[min_index], alist[i]
    return alist


def insert_sort(alist):
    n = len(alist)
    for i in range(1, n):
        if alist[i] < alist[i-1]:
            temp = alist[i]
            j = i-1
            while alist[j]>temp and j >=0:
                alist[j+1] = alist[j]
                j -= 1
            alist[j+1] = temp
    return alist


def shell_sort(alist):
    n = len(alist)
    gap = n
    while gap > 1:
        gap = gap // 3 + 1
        for i in range(gap, n):
            if alist[i] < alist[i-gap]:
                temp = alist[i]
                j = i - gap
                while alist[j] > temp and j >= 0:
                    alist[j+gap] = alist[j]
                    j -= gap
                alist[j+gap] = temp
    return alist


def merge_sort(alist):
    n = len(alist)
    if n <= 1:
        return alist
    left = merge_sort(alist[:n//2])
    right = merge_sort(alist[n//2:])
    if left[-1] > right[0]:
        return mergeing(left, right)
    return alist


def mergeing(list1, list2):
    list1_size = len(list1)
    list2_size = len(list2)
    i = j = 0
    li = []
    while i < list1_size and j < list2_size:
        if list1[i] < list2[j]:
            li.append(list1[i])
            i += 1
        else:
            li.append(list2[j])
            j += 1
    if i < list1_size:
        li.extend(list1[i:])
    if j < list2_size:
        li.extend(list2[j:])
    return li


def quick_sort(alist):
    if len(alist) < 2:
        return alist
    pivot_index = 0
    pivot = alist[pivot_index]
    less_part = [i for i in alist[pivot_index+1:] if i <= pivot]
    great_part = [i for i in alist[pivot_index+1:] if i > pivot]
    return quick_sort(less_part) + [pivot] + quick_sort(great_part)


def partition(alist, beg, end):
    pivot_index = beg  # 第一个元素作为主元的位置
    pivot = alist[pivot_index]
    left = pivot_index + 1
    right = end - 1

    while True:
        while left <= right and alist[left] < pivot:
            left += 1
        while right >= left and alist[right] > pivot:
            right -= 1
        if right < left:
            break
        else:
            alist[left], alist[right] = alist[right], alist[left]
    alist[right], alist[pivot_index] = alist[pivot_index], alist[right]
    return right


def quick_sort_inplace(alist, beg, end):
    if beg < end:
        pivot = partition(alist, beg, end)
        quick_sort_inplace(alist, beg, pivot)
        quick_sort_inplace(alist, pivot+1, end)
        
        
def partition2(alist, beg, end):
    pivot_index = beg
    pivot = alist[pivot_index]

    for i in range(beg + 1, end + 1):
        if alist[i] < pivot:
            alist[pivot_index + 1], alist[i] = alist[i], alist[pivot_index + 1]
            pivot_index += 1
    alist[beg], alist[pivot_index] = alist[pivot_index], alist[beg]
    return pivot_index


def quick_sort2(alist: list, beg: int, end: int):
    if beg >= end:
        return
    pivot_index = partition2(alist, beg, end)
    quick_sort2(alist, beg, pivot_index - 1)
    quick_sort2(alist, pivot_index + 1, end)

def test_quick_sort_inplace():
    import random
    seq = list(range(10))
    random.shuffle(seq)
    quick_sort_inplace(seq, 0, len(seq))
    key = lambda x, y : x <= y
    assert all(key(seq[i], elem) for i, elem in enumerate(seq[1:])) is True

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
