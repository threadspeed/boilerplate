---
title: python script CS166 9-1 Friends Degree experiment (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'CS166 9-1 Friends Degree experiment'

Functions in program: 
* `def calc_average_degree_neighbors(G):`
* `def calc_average_degree(G):`

Modules used in program: 
* `import sys`
* `import random as rd`
* `import networkx as nx`
* `import numpy as np`
* `import matplotlib`
* `import networkx as nx`

## python CS166 9-1 Friends Degree experiment

Python mysql example: CS166 9-1 Friends Degree experiment

```python
import networkx as nx
import matplotlib
matplotlib.use('TkAgg')
# from pylab import *
import numpy as np
import networkx as nx
import random as rd
import sys


# Generate a random network with 1000 nodes and (approximately) 20,000 edges,
# so that the average degree of a node is 40.
n = 1000 # Number of nodes
k = 40 # Degree of nodes
p = k/n #Probabilty of forming an edge
m = int(k/2) #Number of new edges



#  Do this for each of the following types
# of random networks and compare your observations: Erdős­Renyi,
# Watts­Strogatz, Barabási­Albert random graphs.

graph_er = nx.erdos_renyi_graph(n, p)
graph_ws = nx.watts_strogatz_graph(n, k, p=0.2)
graph_ba = nx.barabasi_albert_graph(n, m)


# b. Write code to compute the average degree (which should be 40 — this is just to
# confirm that you generated the graph correctly).
def calc_average_degree(G):
    degrees = [G.degree(i) for i in list(G.nodes)]
    return sum(degrees)/len(degrees)

print('Degree of ER graph: ', calc_average_degree(graph_er))
print('Degree of WS graph: ', calc_average_degree(graph_ws))
print('Degree of BA graph: ', calc_average_degree(graph_ba))


# c. Write code to compute the average degree of each neighbor in the graph. To loop
# through all neighbors in the graph, loop through all edges and then through each
# node attached to an edge.

def calc_average_degree_neighbors(G):
    degrees = [value for value in nx.average_neighbor_degree(G).values()]
    return sum(degrees)/len(degrees)

print('Degree Neighbors of ER graph: ', calc_average_degree_neighbors(graph_er))
print('Degree Neighbors of WS graph: ', calc_average_degree_neighbors(graph_ws))
print('Degree Neighbors of BA graph: ', calc_average_degree_neighbors(graph_ba))



# d. Question: How does the average degree of neighbors (the number of friends of
# your friends) compare to the average degree of the graph (your number of
# friends)

'''
Output:
Degree of ER graph:  40.1
Degree of WS graph:  40.0
Degree of BA graph:  39.2
Degree Neighbors of ER graph:  41.03407015848775
Degree Neighbors of WS graph:  40.161939322542175
Degree Neighbors of BA graph:  60.607995337789106
'''

'''
The average degree of the neighbors is significantly greater than the average
degree of the node for Barabasi Albert Graph. For other graphs it is almost 
similar as the nodes are created randomly. Whereas BA graph actually demonstrates
the actual friend circle between us where some people are more popular than
the others, as a result the popular figure is a common neighbor in many nodes
and we end up getting high degree for neighbors compared to the node.
'''


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
