---
title: python script ALGORITHM LAB KnapSack (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB KnapSack'


## python ALGORITHM LAB KnapSack

Python example: ALGORITHM LAB KnapSack

```python
# knapsack

n=int(input('\n Enter no of items : '))
W=int(input('\n Enter W : '))
item={}
print('\n Enter weights : ')
for i in range(1,n+1):
    item[i]=int(input())
val=[]
val.append(0)
print('\n Enter values  : ')
for i in range(1,n+1):
    v=int(input())
    val.append(v)

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
            M[i][w]=max(M[i-1][w],val[i]+M[i-1][w-item[i]])
#print('ans',M)

for i in range(n+1):
    for w in range(W+1):
        print('For {0},{1} : {2} '.format(i,w,M[i][w]))

# FIND ITEMS IN KNAPSACK
i=n
k=W
knap=[]
while i>0 and k>0 :
    if M[i][k] != M[i-1][k]:
        knap.append(i)
        k=k-item[i]
        i=i-1
    else:
        i=i-1
print('Item numbers in knapsack are : {0}'.format(knap))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
