---
title: python script ALGORITHM LAB Dijstra's (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB Dijstra's'

Functions in program: 
* `def DijstrakS(graph,start):`

## python ALGORITHM LAB Dijstra's

Python mysql example: ALGORITHM LAB Dijstra's

```python
# Dijstra's Algorithm

from heapq import heappush,heappop

def DijstrakS(graph,start):
    A={}
    queue=[(0,start)]
    while queue:
        path_len,v=heappop(queue)
        if v not in A:
            A[v]=path_len
            for w,edge_len in graph[v].items():
                if w not in A:
                    heappush(queue,(edge_len+path_len,w))
    return A
graph={0:{1:6,2:8},1:{4:11},2:{5:7,3:9},3:{},4:{5:3},5:{}}
print(DijstrakS(graph,0))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
