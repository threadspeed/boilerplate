---
title: python script ALGORITHM LAB BFS (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB BFS'

Functions in program: 
* `def bfs(graph, start):`

Modules used in program: 
* `import time`

## python ALGORITHM LAB BFS

Python mysql example: ALGORITHM LAB BFS

```python
# Breadth First Search

import time
a=int(input("number of nodes"))
g={}
for i in range(a):
    print("for",i+1,"enter all the conecting nodes:",)
    b=list(map(int,input().split()))
    for j in b:
        if i+1 not in g:
            g.update({i+1:[j]})
        else:
            g[i+1].append(j)
def bfs(graph, start):
    visited, queue = [], [start]
    while queue:
        vertex = queue.pop(0)
        if vertex not in visited:
            visited.append(vertex)
            queue.extend([i for i in graph[vertex] if i not in visited])
    return visited
s=int(input("starting point of graph"))
start_time=time.clock()
print(bfs(g,s))
print(time.clock()-start_time)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
