---
title: python script Algorithm Hanoi (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Algorithm Hanoi'

Functions in program: 
* `def Hanoi_Recursion(n,A,B,C):`

## python Algorithm Hanoi

Python mysql example: Algorithm Hanoi

```python
def Hanoi_Recursion(n,A,B,C):
    if n==1:
        print("將第", n, "個圓盤由", A, "移到", C)
        return
    Hanoi_Recursion(n-1,A,C,B)
    print("將第", n, "個圓盤由", A, "移到", C)
    Hanoi_Recursion(n-1,B,A,C)


Hanoi_Recursion(4,'A','B','C')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
