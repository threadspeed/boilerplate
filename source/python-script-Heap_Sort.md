---
title: python script Heap Sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Heap Sort'

Functions in program: 
* `def main():`
* `def heap_sort(A):`
* `def build_max_heap(A):`
* `def max_heapify(A,i):`

Modules used in program: 
* `import timeit`

## python Heap Sort

Python mysql example: Heap Sort

```python
# This is the implementation of heap sort algorithm as given in the "Introduction To Algorithms" Thomas H. Cormen,
# Charles E. Leiserson, Ronald L. Rivest, Clifford Stein

import timeit
# import random                                 # If using random function for input

def max_heapify(A,i):
    l=2*i
    r=(2*i)+1
    if l<=len(A)-1 and A[l]>A[i]:
        largest=l
    else:
        largest=i
    if r<=len(A)-1 and A[r]>A[largest]:
        largest=r
    if largest != i:
        A[i],A[largest]=A[largest],A[i]
        A=max_heapify(A,largest)
    return A

def build_max_heap(A):
    l=len(A)-1
    for i in range(l/2,0,-1):
        A=max_heapify(A,i)
    return A

def heap_sort(A):
    A=build_max_heap(A)
    l=len(A)
    B=[]
    for i in range(len(A)-1,1,-1):
        A[1],A[i]=A[i],A[1]
        l=l-1
        B.insert(0,A[l])
        A=max_heapify(A[:l],1)
    B.insert(0,A[1])
    return B

def main():
    f = open('input.txt', 'r')              # Taking from a txt file named input
    # File is of format 2,45, and so on. That is comma separated values
    A = []
    for ch in f:
        A = ch.split(',')                   # Split the characters in file
    f.close()
    A = [int(x) for x in A]                 # Characters were of type 'string', converting them to 'int'
    # A=random.sample(xrange(10000), 200)   # If you want to take random input. 200 tells the size of array.
    print("Unsorted list")
    print(A)
    A.insert(0,'adjustlist')                # Putting a random value in A[0] of array, just to make other loops easy
    print("Sorted List")
    start = timeit.default_timer()
    print(heap_sort(A))
    stop = timeit.default_timer()
    print("running time")
    print(stop - start)


if __name__=="__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
