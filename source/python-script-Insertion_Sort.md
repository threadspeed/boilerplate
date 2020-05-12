---
title: python script Insertion Sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Insertion Sort'

Functions in program: 
* `def main():`
* `def insertion_sort(A):`

Modules used in program: 
* `import timeit`

## python Insertion Sort

Python mysql example: Insertion Sort

```python
# This is the implementation of insertion sort algorithm as given in the "Introduction To Algorithms" Thomas H. Cormen,
# Charles E. Leiserson, Ronald L. Rivest, Clifford Stein

import timeit
# import random                                 # If using random function for input

def insertion_sort(A):
    for j in range(1, len(A) ):
        key = A[j]
        i = j - 1
        while i >= 0 and A[i] > key:
            A[i + 1] = A[i]
            i = i - 1
        A[i + 1] = key
    return A


def main():
    f = open('input.txt', 'r')                  # Taking from a txt file named input
    # File is of format 2,45, and so on. That is comma separated values
    A = []
    for ch in f:
        A = ch.split(',')                       # Split the characters in file
    f.close()
    A = [int(x) for x in A]                     # Characters were of type 'string', converting them to 'int'
    # A=random.sample(xrange(10000), 200)       # If you want to take random input. 200 tells the size of array.
    print("Unsorted list")
    print(A)
    print("Sorted List")
    start = timeit.default_timer()
    print(insertion_sort(A))
    stop = timeit.default_timer()
    print("running time")
    print(stop - start)


if __name__ == "__main__":
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
