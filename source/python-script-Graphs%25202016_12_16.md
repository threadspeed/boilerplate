---
title: python script Graphs%25202016 12 16 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Graphs%25202016 12 16'


Modules used in program: 
* `import random`
* `import math`
* `import queue`
* `import functools`
* `import operator`
* `import random`

## python Graphs%25202016 12 16

Python example: Graphs%25202016 12 16

```python

# coding: utf-8

# This is an implementation of a graph in python 3. DFS, BFS and Dijkstra are implemented. A start has been made on Prim's algorithm. A* is implemented on the MapGraph object, which is a Graph object with extra constraints.

# In[2]:

# Implementing a graph list using edge and vertex objects, idea from: Wikipedia, Michael T. Goodrich and Roberto Tamassia (2002). Algorithm Design: Foundations, Analysis, and Internet Examples. John Wiley & Sons. ISBN 0-471-38365-1.

from first import first

class Vertex(object):
    
    def __init__(self, value):
        self.value = value
        # Only want unique routes.
        self.edges = set()
        
    def connect(self, other, weight=1, directional=False):
        edge = Edge(self, other, weight=weight)
        self.edges.add(edge)
        if not directional:
            other.edges.add(Edge(other, self, weight=weight))
            
    def __str__(self):
        return '{} -> [{}]'.format(self.value, ', '.join(e.bsc_str for e in self.edges)) 
    
    def __repr__(self):
        return str(self)
    
    def __gt__(self, other):
        return self.value > other.value
    
    def __lt__(self, other):
        return self.value < other.value
    
    @property
    def bsc_str(self):
        return str(self.value)
    
    def get_neighbours(self, seen=None, path=None):
        if not path:
            path = Path()
        if seen is None:
            seen = []
        neighbours = [(e.to_vertex, path.add(e)) for e in
                      sorted(self.edges, reverse=True) if e.to_vertex not in seen]
        return neighbours
    
    @property
    def neighbours(self):
        return [v for v, s in self.get_neighbours()]
        
class Edge(object):
    
    """Directional edge object."""
    
    def __init__(self, from_vertex, to_vertex, weight=1):
        self.from_vertex = from_vertex
        self.to_vertex = to_vertex
        if callable(weight):
            weight = weight(from_vertex, to_vertex)
        if weight < 1:
            raise Exception('Weight must be 1 or higher.')
        self.weight = weight
        
    def __str__(self):
        weight = '({})'.format(self.weight)
        return '{from_v} -{weight}> {to_v}'.format(from_v=self.from_vertex.bsc_str, weight=weight,
                                                   to_v=self.to_vertex.bsc_str)
    
    @property
    def bsc_str(self):
        return '({})>{}'.format(self.weight, self.to_vertex.bsc_str)
    
    def __repr__(self):
        return str(self)
    
    def __key(self):
        return (self.from_vertex, self.to_vertex, self.weight)

    def __eq__(self, other):
        return  self.__key() == other.__key()
    
    def __lt__(self, other):
        return self.weight < other.weight
    
    def __hash__(self):
        return hash(self.__key())
    

class Path(object):
    
    def __init__(self, path=None):
        if not path:
            self.path = []
        else:
            self.path = path
        
    def add(self, edge):
        return Path(self.path + [edge])
    
    def __len__(self):
        return sum(e.weight for e in self.path)
    
    def __lt__(self, other):
        if isinstance(other, NoPath):
            return True
        return len(self) < len(other)
    
    def __gt__(self, other):
        if isinstance(other, NoPath):
            return False
        return len(self) > len(other)
    
    def __str__(self):
        return str(self.path)
    
    def __repr__(self):
        return str(self)
    
    def __eq__(self, other):
        return self.path == other.path
    
    def end(self):
        if self.path:
            return self.path[-1].to_vertex
        
    def start(self):
        if self.path:
            return self.path[0].from_vertex
    
class NoPath(Path):
    
    """Indicates that no path exists.
    
    Has a length of infinity.
    """
    def length(self):
        return float('infinity')
    
    def __len__(self):
        return 0
    
    def __lt__(self, other):
        return False
    
    def __gt__(self, other):
        return True
    
    def __boolean__(self):
        """NoPath is Falsy."""
        return False
    
    def __str__(self):
        return '[<>]'
    
    def __eq__(self, other):
        if isinstance(other, NoPath):
            return True

    
class Graph(object):
    
    def __init__(self, vertex=None):
        self.vertexes = []
        if vertex is not None:
            self.add_vertex(vertex)
            
    def add_vertex(self, value):
        if value in self:
            return
        if not isinstance(value, Vertex):
            value = Vertex(value)
        self.vertexes.append(value)
        
    def connect_vertexes(self, one, other, weight=1, directional=False):
        self[one].connect(self[other], weight, directional)
            
    def __getitem__(self, key):
        if isinstance(key, Vertex):
            key = key.value
        item = first(v for v in self.vertexes if v.value == key)
        if item:
            return item
        else:
            raise IndexError('Unknown vertex {}.'.format(key))
            
    def bfs(self, start, end):
        """Do a breath first search for start and end node."""
        seen = set()
        end = self[end]
        # Make this a stack, as popping from a list can be expensive.
        test = [(self[start], None)]
        while True:
            if not test:
                return NoPath()
            # Get the first added vertex.
            vertex, path = test.pop(0)
            if vertex == end:
                return path
            seen.add(vertex)
            neighbours = vertex.get_neighbours(seen=seen, path=path)
            test.extend(neighbours)

    
    def dfs(self, start, end):
        """Do a depth first search for start and end node."""
        seen = set()
        end = self[end]
        # Make this a queue, as popping from a list can be expensive.
        test = [(self[start], None)]
        while True:
            if not test:
                return NoPath()
            # Get the last added vertex.
            vertex, path = test.pop()
            if vertex == end:
                return path
            seen.add(vertex)
            neighbours = vertex.get_neighbours(seen, path)
            test.extend(neighbours)
            
    def dijkstra(self, start):
        pass
    
    def dijkstra_path(self, start, end):
        not_seen = set(self.vertexes)
        # TODO make cost_table a priority queue.
        cost_table = dict.fromkeys(self.vertexes, NoPath())
        cost_table[self[start]] = Path()
        end = self[end]
        while True:
            if not_seen.issubset(k for k, v in cost_table.items() if v == NoPath()):
                break
            # This is sorting on every loop, and thus is very in effecient.
            vertex, current_path = first(sorted(((k, v) for k, v in cost_table.items() if k in not_seen),
                                         key=lambda v: v[1]))
            not_seen.remove(vertex)
            for neighbour, path in vertex.get_neighbours(path=current_path):
                if cost_table[neighbour] > path:
                    cost_table[neighbour] = path
        path = cost_table[end]
        if path.start() == self[start]:
            return cost_table[end]
        return NoPath()
        
    def prims(self, start):
        seen = set()
        tree = []
        # Make this a priority queue.
        test = [(0, Path(), start)]
        while True:
            if not test:
                break
            _, current_path, vertex = heappop(test)
            seen.add(vertex)
            for edge in vertex.edges:
                if edge.to_vertex not in seen:
                    heappush(
                        test,
                        (edge.weight, current_path.add(e), edge.to_vertex)
                    )
        pass
        
    def __iter__(self):
        return iter(self.vertexes)
        
    def __len__(self):
        return len(self.vertexes)
        
    def __contains__(self, key):
        if isinstance(key, Vertex):
            key = key.value
        return first(v for v in self.vertexes if v.value == key) and True
        
    def __str__(self):
        return '\n'.join(str(v) for v in self.vertexes)
    
    def __repr__(self):
        return str(self)


# In[104]:

import random
import operator
import functools
import queue
import math

class MapGraph(Graph):
    
    def __init__(self, size=8):
        self.size = size
        super().__init__()
        for x in range(size):
            for y in range(size):
                self.add_vertex((x, y))
    
    def random_connect(self, connection_chance=0.5, weight=lambda f, t: random.randint(1, 3), diagonals=True):
        dirs = ((-1, 0), (0, -1), (0, 1), (1, 0))
        if diagonals:
            dirs = dirs + ((-1, -1), (-1, 1), (1, -1), (1, 1))
        for v in self.vertexes:
            for i in dirs:
                p = tuple(map(operator.add, v.value, i))
                if random.random() <= connection_chance:
                    try:
                        self.connect_vertexes(v, p, weight=weight, directional=True)
                    except IndexError:
                        pass
                    
    def a_star(self, start, end, h=lambda p, e: math.sqrt((p[0] - e[0])**2 + (p[1] - e[1])**2)):
        start = self[start]
        end = self[end]
        seen = set()
        test = queue.PriorityQueue()
        test.put((h(start.value, end.value), start, None))
        while True:
            if test.empty():
                return NoPath()
            _, vertex, path = test.get()
            seen.add(vertex)
            neighbours = vertex.get_neighbours(seen, path=path)
            for n, p in neighbours:
                if n == end:
                    return p
                hv = len(p) + h(n.value, end.value)
                test.put((hv, n, p))


# In[128]:

m = MapGraph()
m.random_connect(weight=1, connection_chance=0.7, diagonals=False)
#print(m)t
print(m.dijkstra_path((0,0), (4,5)))
m.a_star((0,0), (4,5))


# In[3]:

import random

g = Graph()
for i in range(6):
    g.add_vertex(i)
    
for v in g:
    for _ in range(random.randrange(4)):
        g.connect_vertexes(v, random.randrange(len(g)), directional=True, weight=random.randint(1, 5))
#print(g)

print(g)
print('bfs:', g.bfs(0,2))
print('dfs', g.dfs(0,2))
print('dijkstra', g.dijkstra_path(0,2))


# In[47]:

v1.edges.pop()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
