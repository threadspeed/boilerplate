---
title: python script ALGORITHM LAB Bellman%2520Ford (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ALGORITHM LAB Bellman%2520Ford'

Functions in program: 
* `def bellman(g,vertex,s):`

## python ALGORITHM LAB Bellman%2520Ford

Python mysql example: ALGORITHM LAB Bellman%2520Ford

```python
# Bellman Ford

def bellman(g,vertex,s):
    a={}
    for i in vertex:
        a[i]=0 if i==s else float('inf')#Source=0 rest are infinite
    for i in range(len(vertex)):#Till N-1 Vertex
        for u,v,w in g:#For each edge(u,v,w)
            if (a[u]+w)<a[v]:
                a[v]=a[u]+w
    return a
vertex=[1,2,3,4,5]
g={(2,1,-3),(4,2,1),(5,2,4),(5,4,-2),(4,3,1),(3,4,2),(1,3,6),(1,4,3)}#g={Vertex1,Vertex2,Weight}
src=int(input("Enter the souce: "))
a=bellman(g,vertex,src)
#print(a)
for i in a:
    print("Distance of Path From Source Vertex {0} to Dest Vertex {1} is {2}".format(src,i,a[i]))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
