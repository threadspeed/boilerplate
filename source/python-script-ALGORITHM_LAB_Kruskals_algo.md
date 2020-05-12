---
title: python script ALGORITHM LAB Kruskals algo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB Kruskals algo'

Functions in program: 
* `def kruskal(g,vertex):`

## python ALGORITHM LAB Kruskals algo

Python mysql example: ALGORITHM LAB Kruskals algo

```python
# Kruskals Algorithm

def kruskal(g,vertex):
    t,a=[],{}
    for i in vertex:
        a[i]=set({i})
    for edge in sorted(g):
        for v1,v2 in g[edge]:
            if v1 not in a[v2]:
                t.append((v1,v2,edge))
                a[v1]=a[v1].union(a[v2])
                for i in a[v1]:
                    a[i]=a[v1]
    return t
#g={20,:[[2],[2,0]],1:[[0,1],[1,0]],3:[[1,2],[2,1]]}# g={weight:[Vertex1,Vertex2]...}
g={2:[[1,2],[2,1]],1:[[2,3],[3,2]],2:[[1,3],[3,1]],5:[[2,4],[4,2]],3:[[3,4],[4,3]]}
vertex=[1,2,3,4]#Vertex list
a=kruskal(g,vertex)#returns list of vertex(u,v) which is in resulting Spanning Tree
#print(a)
print("The Spanning tree is ")
for i in a: print("Vertex(U) {0} to Vertex(V) {1} with Weight {2}".format(i[0],i[1],i[2]))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
