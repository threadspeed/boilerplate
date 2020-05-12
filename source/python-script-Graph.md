---
title: python script Graph (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Graph'


## python Graph

Python mysql example: Graph

```python
"""from Ch2 of think complexity."""

class Graph(dict):
  def __init__(self, vertices=[], edges=[]):
    for vertex in vertices:
      self.add_vertex(vertex)
    for edge in edges:
      self.add_edge(edge)

  def add_vertex(self, vertex):
    self[vertex] = {}

  def add_edge(self, edge):
    v, w = edge
    self[v][w] = edge
    self[w][v] = edge

  def get_edge(self, v, w):
    try:
      return self[v][w]
    except:
      return None

  def remove_edge(self, edge):
    self[edge[0]][edge[1]] = None
    self[edge[1]][edge[0]] = None

  def vertices(self):
    return self.keys()

  def edges(self):
    all_vertices = self.vertices()
    all_edges = []
    for v in all_vertices:
      for w in all_vertices:
        all_edges.append(self.get_edge(v, w))
    return [e for e in set(all_edges) if e is not None]

  def out_vertices(self, vertex):
    edges = [self.get_edge(v, vertex) for v in self.vertices()]
    vertices = []
    for e in edges:
      if e is None:
        continue
      if e[0] == vertex:
        vertices.append(e[1])
      elif e[1] == vertex:
        vertices.append(e[0])
    return vertices

  def out_edges(self, vertex):
    edges = [e for e in self.edges() if vertex in e]
    return list(set(edges))
  
  def add_all_edges(self):
    all_vertices = self.vertices()
    while all_vertices:
      v = all_vertices.pop()
      for w in all_vertices:
        edge = Edge(v, w)
        self.add_edge(edge)

  def add_regular_edges(self, degree):
    number_of_vertices = len(self.vertices())
    if number_of_vertices < degree + 1:
      raise ValueError('too high of a degree')
    if (number_of_vertices * degree) % 2 != 0:
      raise ValueError('n * degree must be even')

    # via http://math.stackexchange.com/questions/142112
    for index in range(number_of_vertices):
      if degree % 2 == 0:
        number_of_neighbors_per_side = degree / 2
      else:
        number_of_neighbors_per_side = (degree - 1) / 2
        # and connect the vertex directly opposed to this vertex
        target_index = (index + number_of_vertices / 2) % number_of_vertices
        edge = Edge(self.vertices()[index], self.vertices()[target_index])
        self.add_edge(edge)
      for j in range(number_of_neighbors_per_side):
        target_index = (index + j + 1) % number_of_vertices
        edge = Edge(self.vertices()[index], self.vertices()[target_index])
        self.add_edge(edge)
        target_index = (index - j + 1) % number_of_vertices
        edge = Edge(self.vertices()[index], self.vertices()[target_index])
        self.add_edge(edge)


class Vertex(object):
  def __init__(self, label=''):
    self.label = label

  def __repr__(self):
    return 'Vertex(%s)' % repr(self.label)


class Edge(tuple):
  def __new__(cls, e1, e2):
    return tuple.__new__(cls, (e1, e2))

  def __repr__(self):
    return 'Edge(%s, %s)' % (repr(self[0]), repr(self[1]))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
