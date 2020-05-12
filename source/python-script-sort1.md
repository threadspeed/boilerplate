---
title: python script sort1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sort1'

Functions in program: 
* `def perform_quick_sort(alist, beg, end):`
* `def quick_sort(alist):`
* `def merge(left, right):`
* `def merge_sort2(alist):`
* `def merge_sort1(alist):`
* `def shell_sort(alist):`
* `def insert_sort(alist):`
* `def select_sort(alist):`
* `def bubble_sort(alist):`
* `def is_sorted(alist):`

Modules used in program: 
* `import random`
* `import random`
* `import random`
* `import random`
* `import random`
* `import random`
* `import random`

## python sort1

Python example: sort1

```python
#!/usr/bin/env python3


def is_sorted(alist):
    n = len(alist)
    if n == 1 or n == 0:
        return True

    for i in range(1, n):
        if alist[i] < alist[i - 1]:
            return False
    return True


def bubble_sort(alist):
    """冒泡排序"""
    n = len(alist)
    if n == 1 or n == 0:
        return alist

    for i in range(n - 1):
        sorted = True
        for j in range(1, n - i):
            if alist[j] < alist[j - 1]:
                alist[j], alist[j - 1] = alist[j - 1], alist[j]
                sorted = False
        if sorted:
            return alist
    return alist


print("=*" * 9, "冒泡排序", "=*" * 9)
import random

alist = list(range(10))
random.shuffle(alist)
print("排序前", alist)
bubble_sort(alist)
print("排序后", alist, ", is sorted {}".format(is_sorted(alist)))
print("\n" * 3)


def select_sort(alist):
    """选择排序"""
    n = len(alist)
    if n == 1 or n == 0:
        return alist

    for i in range(n - 1):
        min = i
        for j in range(i + 1, n):
            if alist[j] < alist[min]:
                min = j
        if min != i:
            alist[i], alist[min] = alist[min], alist[i]
    return alist


print("=*" * 9, "选择排序", "=*" * 9)
import random

alist = list(range(10))
random.shuffle(alist)
print("排序前", alist)
select_sort(alist)
print("排序后", alist, ", is sorted {}".format(is_sorted(alist)))
print("\n" * 3)


def insert_sort(alist):
    """插入排序"""
    n = len(alist)
    if n == 1 or n == 0:
        return alist

    for i in range(1, n):
        j = i
        while j > 0:
            if alist[j] < alist[j - 1]:
                alist[j], alist[j - 1] = alist[j - 1], alist[j]
                j -= 1
            else:
                break
    return alist


print("=*" * 9, "插入排序", "=*" * 9)
import random

alist = list(range(10))
random.shuffle(alist)
print("排序前", alist)
insert_sort(alist)
print("排序后", alist, ", is sorted {}".format(is_sorted(alist)))
print("\n" * 3)


def shell_sort(alist):
    """希尔排序"""
    n = len(alist)
    if n == 1 or n == 0:
        return alist

    gap = n // 2
    while gap >= 1:
        for i in range(gap, n):
            j = i
            while j > 0:
                if alist[j] < alist[j - gap]:
                    alist[j], alist[j - gap] = alist[j - gap], alist[j]
                    j -= gap
                else:
                    break
        gap //= 2
    return alist


print("=*" * 9, "希尔排序", "=*" * 9)
import random

alist = list(range(10))
random.shuffle(alist)
print("排序前", alist)
shell_sort(alist)
print("排序后", alist, ", is sorted {}".format(is_sorted(alist)))
print("\n" * 3)


def merge_sort1(alist):
    """归并排序, 无辅助函数"""
    n = len(alist)
    if n == 1 or n == 0:
        return alist

    mid = n // 2

    # left 采用归并排序后形成的新的有序列表
    left_li = merge_sort1(alist[:mid])
    # right 采用归并排序后形成的新的有序列表
    right_li = merge_sort1(alist[mid:])

    # merge(left, right)将两个有序子序列合并为一个新的整体
    left_pointer = right_pointer = 0
    result = []

    while left_pointer < len(left_li) and right_pointer < len(right_li):
        if left_li[left_pointer] < right_li[right_pointer]:
            result.append(left_li[left_pointer])
            left_pointer += 1
        else:
            result.append(right_li[right_pointer])
            right_pointer += 1
    result.extend(left_li[left_pointer:])
    result.extend(right_li[right_pointer:])
    return result


print("=*" * 9, "归并排序, 无辅助函数", "=*" * 9)
import random

alist = list(range(10))
random.shuffle(alist)
print("排序前", alist)
alist = merge_sort1(alist)
print("排序后", alist, ", is sorted {}".format(is_sorted(alist)))
print("\n" * 3)


def merge_sort2(alist):
    """归并排序，有辅助函数"""
    n = len(alist)
    if n == 1 or n == 0:
        return alist

    mid = n // 2
    left = merge_sort2(alist[:mid])
    right = merge_sort2(alist[mid:])

    return merge(left, right)


def merge(left, right):
    left_pointer = right_pointer = 0
    result = []
    while left_pointer < len(left) and right_pointer < len(right):
        if left[left_pointer] < right[right_pointer]:
            result.append(left[left_pointer])
            left_pointer += 1
        else:
            result.append(right[right_pointer])
            right_pointer += 1
    result.extend(left[left_pointer:])
    result.extend(right[right_pointer:])
    return result


print("=*" * 9, "归并排序, 有辅助函数", "=*" * 9)
import random

alist = list(range(10))
random.shuffle(alist)
print("排序前", alist)
alist = merge_sort2(alist)
print("排序后", alist, ", is sorted {}".format(is_sorted(alist)))
print("\n" * 3)


def quick_sort(alist):
    """快速排序"""
    n = len(alist)
    if n == 1 or n == 0:
        return alist
    perform_quick_sort(alist, 0, n-1)
    return alist


def perform_quick_sort(alist, beg, end):
    if beg >= end:
        return

    pivot = alist[beg]
    low = beg
    high = end

    while high > low:
        while high > low and alist[high] >= pivot:
            high -= 1
        alist[low] = alist[high]
        while high > low and alist[low] < pivot:
            low += 1
        alist[high] = alist[low]
    alist[low] = pivot  # 当循环退出时，low=high
    perform_quick_sort(alist, beg, low-1)
    perform_quick_sort(alist, low+1, end)


print("=*" * 9, "快速排序", "=*" * 9)
import random
alist = list(range(10))
random.shuffle(alist)
print("排序前", alist)
quick_sort(alist)
print("排序后", alist, ", is sorted {}".format(is_sorted(alist)))
print("\n" * 3)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
