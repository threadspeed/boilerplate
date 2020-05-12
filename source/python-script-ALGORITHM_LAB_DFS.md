---
title: python script ALGORITHM LAB DFS (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB DFS'

Functions in program: 
* `def DFS(g,start,path=[]):`

Modules used in program: 
* `import time`

## python ALGORITHM LAB DFS

Python mysql example: ALGORITHM LAB DFS

```python
# Deapth First Search

import time
a=int(input("number of nodes"))
g={}
for i in range(a):
    print("for",i+1)
    b=list(map(int,input().split()))
    for j in b:
        if i+1 not in g:
            g.update({i+1:[j]})
        else:
            g[i+1].append(j)
def DFS(g,start,path=[]):
    path.append(start)
    for i in g[start]:
        if i not in path:
            y=DFS(g,i,path)
    return path
start=int(input("enter the start node"))
start_time=time.clock()
print(DFS(g,start))
print(time.clock()-start_time)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
