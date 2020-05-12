---
title: python script inversion (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'inversion'

Functions in program: 
* `def merge_sort(a,k):`
* `def merge(a,b,k=0):`

Modules used in program: 
* `import time`
* `import random`

## python inversion

Python example: inversion

```python
import random
import time
n=int(input('Enter the numbers'))
a=[random.randint(0,100) for i in range(n)]
def merge(a,b,k=0):
    i,j,c=0,0,[]
    while((i<len(a)) and j<len(b)):
        if a[i]<b[j]:
            c.append(a[i])
            i=i+1
        else:
            c.append(b[j])
            j=j+1
            k=k+len(a)-i
    while(i<len(a)):
        c.append(a[i])
        i=i+1
    while(j<len(b)):
        c.append(b[j])
        j=j+1
    return c,k
def merge_sort(a,k):
    if (len(a)>1):
        a1,k=merge_sort(a[0:len(a)//2],k)
        b1,k=merge_sort(a[len(a)//2:],k)
        a,k=merge(a1,b1,k)
    return a,k
print(a)
start_time=time.clock()
print('count=',merge_sort(a,0)[1])
print(time.clock()-start_time)




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
