---
title: python script ALGORITHM LAB SUBSET SUM (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB SUBSET SUM'


## python ALGORITHM LAB SUBSET SUM

Python example: ALGORITHM LAB SUBSET SUM

```python
# Subset Sum

n=int(input('\n Enter no of items : '))
W=int(input('\n Enter W : '))
#w=list(map(int,input('\n weights :').split()))
item={}
for i in range(1,n+1):
    item[i]=int(input('\n weights :'))
M={}
for i in range(max(n,W)):
    M[i]={}
for i in range(n+1):
    M[i][0]=0
for w in range(W+1):
    M[0][w]=0
for i in range(1,n+1):
    for w in range(1,W+1):
        if(item[i]>w):
            M[i][w]=M[i-1][w]
        else :
            M[i][w]=max(M[i-1][w],item[i]+M[i-1][w-item[i]])
#print('ans',M)

for i in range(n+1):
    for w in range(W+1):
        print('For {0},{1} : {2} '.format(i,w,M[i][w]))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
