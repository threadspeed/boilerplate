---
title: python script bfs (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bfs'

Functions in program: 
* `def bfs(graph,start):`

## python bfs

Python mysql example: bfs

```python
a=int(input('Enter the nodes'))
g={}
for i in range(a):
    print('For',i+1,'Enter all the connecting nodes')
    b = list(map(int,input().split()))
    for j in b:
        if i+1 not in g:
            g.update({i+1:[j]})
        else:
            g[i+1].append(j)
def bfs(graph,start):
    visited,queue=[],[start]
    while queue:
        vertex=queue.pop(0)
        if vertex not in visited:
            visited.append(vertex)
            queue.extend([i for i in graph[vertex] if i not in visited])
    return visited
s=int(input('Enter the starting node'))
print(bfs(g,s))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
