---
title: python script Merge Sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Merge Sort'

Functions in program: 
* `def main():`
* `def merge_sort(Array):`
* `def merge(left, right):`

Modules used in program: 
* `import timeit`

## python Merge Sort

Python example: Merge Sort

```python
# This is the implementation of merge sort algorithm as given in the "Introduction To Algorithms" Thomas H. Cormen,
# Charles E. Leiserson, Ronald L. Rivest, Clifford Stein

import timeit
# import random                                 # If using random function for input

def merge(left, right):
    size1 = len(left)
    size2 = len(right)
    if not size1 or not size2:
        return left or right
    result = []
    i, j = 0, 0
    while (len(result) < size1 + size2):
        if left[i] < right[j]:
            result.append(left[i])
            i += 1
        else:
            result.append(right[j])
            j += 1
        if i == size1 or j == size2:
            result.extend(left[i:] or right[j:])
            break
    return result

def merge_sort(Array):
    r=len(Array)
    A=Array
    left=[]
    right=[]
    if r<2:
        return A
    q=r/2
    left=merge_sort(A[:q])
    right=merge_sort(A[q:])
    B=merge(left,right)
    return B

def main():
    f = open('input.txt', 'r')				# Taking from a txt file named input
    # File is of format 2,45, and so on. That is comma separated values
    A=[]
    for ch in f:
        A=ch.split(',')						# Split the characters in file
    f.close()
    A=[int(x) for x in A]					# Characters were of type 'string', converting them to 'int'
    # A=random.sample(xrange(10000), 200)   # If you want to take random input. 200 tells the size of array.
    print("Unsorted list")
    print(A)
    print("Sorted List")
    start = timeit.default_timer()			# To time the time take by the sort
    print(merge_sort(A))
    stop = timeit.default_timer()
    print("running time")
    print(stop-start)

if __name__=="__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
