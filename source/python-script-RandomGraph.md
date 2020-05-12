---
title: python script RandomGraph (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'RandomGraph'


Modules used in program: 
* `import random`

## python RandomGraph

Python example: RandomGraph

```python
import random

from Graph import Graph
from Graph import Edge


class RandomGraph(Graph):
  def add_random_edges(self, probability):
    all_vertices = self.vertices()
    while all_vertices:
      v = all_vertices.pop()
      for w in all_vertices:
        if random.random() <= probability:
          edge = Edge(v, w)
          self.add_edge(edge)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
