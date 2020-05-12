---
title: python script Quick Sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Quick Sort'

Functions in program: 
* `def main():`
* `def quick_sort(A,p,r):`
* `def partition(A,p,r):`

Modules used in program: 
* `import timeit`

## python Quick Sort

Python example: Quick Sort

```python
# This is the implementation of quick sort algorithm as given in the "Introduction To Algorithms" Thomas H. Cormen,
# Charles E. Leiserson, Ronald L. Rivest, Clifford Stein

import timeit
# import random                                 # If using random function for input

def partition(A,p,r):
    x=A[r]
    i=p-1
    for j in range(p,r):
        if A[j]<=x:
            i=i+1
            A[i],A[j]=A[j],A[i]
    A[i+1],A[r]=A[r],A[i+1]
    return i+1

def quick_sort(A,p,r):
    if p<r:
        q=partition(A,p,r)
        quick_sort(A,p,q-1)
        quick_sort(A,q+1,r)
    return A

def main():
    f = open('input.txt', 'r')               # Taking from a txt file named input
    # File is of format 2,45, and so on. That is comma separated values
    A = []
    for ch in f:
        A = ch.split(',')                    # Split the characters in file
    f.close()
    A = [int(x) for x in A]                  # Characters were of type 'string', converting them to 'int'
    # A=random.sample(xrange(10000), 200)    # If you want to take random input. 200 tells the size of array.
    print("Unsorted list")
    print(A)
    print("Sorted List")
    start = timeit.default_timer()
    print(quick_sort(A,0,len(A)-1))
    stop = timeit.default_timer()
    print("running time")
    print(stop - start)


if __name__=="__main__":
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
