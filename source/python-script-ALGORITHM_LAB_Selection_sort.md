---
title: python script ALGORITHM LAB Selection sort (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB Selection sort'

Functions in program: 
* `def sort(a):`

## python ALGORITHM LAB Selection sort

Python mysql example: ALGORITHM LAB Selection sort

```python
# SELECTION SORT

def sort(a):
    global min,temp
    for i in range(len(a)-1) :
        min=i
        for j in range(i+1,len(a)):
            if a[j]<a[min]:
                min=j

        temp=a[i]
        a[i]=a[min]
        a[min]=temp



lst=list(map(int,input('enter : ').split()))
print(lst)
sort(lst)
print("sorted : ",lst)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
