---
title: python script samllworldgraph (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'samllworldgraph'


## python samllworldgraph

Python mysql example: samllworldgraph

```python
from RandomGraph import RandomGraph,show_graph
from Graph import *
from random import random, randint, choice
from collections import deque


class SmallWorldGraph(RandomGraph):

    def rewire(self, p):
        vs = self.vertices()
        for i, v in enumerate(vs):
            for e in self.out_edges(v):
                if random() <= p:
                    without_v = vs[:i]+vs[i+1:]
                    w = choice(without_v)
                    self.remove_edge(e)
                    e = Edge(v,w)
                    self.add_edge(e)


    def clustering_coefficient(self):
        vs = self.vertices()
        total = []
        for v in vs:
            E = self.traid(v)
            Z = self.max_of_traid(v)
            if Z == 0:
                total.append(0)
            else:
                total.append(E/Z)
        return 1.0 * sum(total)/len(total)

    def traid(self, v):
        """check number of group that v is connected to other 
        2 nodes triangly"""
        count = 0
        adj_v = self.out_vertices(v)
        for i, v in enumerate(adj_v):
            for w in adj_v[i:]:
                if self.has_edge(v, w):
                    count += 1
        return count

    def max_of_traid(self, v):
        """return maximam of traid of nodes (v)"""
        adj_v = self.out_vertices(v)
        k = len(adj_v)
        return k * (k - 1) / 2.0

    def ave_path_length(self):
        """return average path length of graph"""
        vs = self.vertices()
        k = len(vs)
        total = []
        for i, v in enumerate(vs):
            for w in vs[i:]:
                d = self.simple_dijkstra(v, w)
                total.append(d)
        return  1.0 * sum(total) / len(total)

    def simple_dijkstra(self, v, w):
        """this is simplyfid dijkstra which considers all edges is
        the same length. return distance between v and w
        (v) is a starting vertex, (w) is a goal vertex"""
        v.d = 0
        worklist = deque([v])
        dist = self.distance
        visited = set()
        while worklist:
            v = worklist.popleft()
            visited.add(v)
            if v is w:
                return v.d
            unvisit = [dist(u,v) for u in self.out_vertices(v) 
                        if u not in visited and v not in worklist]
            worklist.extend(unvisit)
        return 0

    def distance(self, u, v):
        """add distance to an unvisted vertex (u)"""
        u.d = v.d + 1
        return u

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
