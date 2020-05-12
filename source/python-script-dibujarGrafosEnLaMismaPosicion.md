---
title: python script dibujarGrafosEnLaMismaPosicion (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dibujarGrafosEnLaMismaPosicion'

Functions in program: 
* `def printGraph(G, pos):`

Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import random`
* `import networkx as nx`

## python dibujarGrafosEnLaMismaPosicion

Python mysql example: dibujarGrafosEnLaMismaPosicion

```python
#!/usr/bin/python3
# -*- coding: utf-8 -*-

import networkx as nx
import random
import matplotlib.pyplot as plt


def printGraph(G, pos):
    labels = nx.get_edge_attributes(G, 'weight')
    # positions for all nodes
    # nodes
    nx.draw_networkx_nodes(G, pos, node_size=700)
    # edges
    nx.draw_networkx_edges(G, pos, width=4)
    # labels
    nx.draw_networkx_labels(G, pos, font_size=20, font_family='sans-serif')
    labels = nx.get_edge_attributes(G, 'weight')
    nx.draw_networkx_edge_labels(G, pos, edge_labels=labels)
    plt.axis('off')
    plt.show()


# grafo de n nodos donde la probabilidad de que un eje exista es de p
n = 5
G = nx.complete_graph(n)
for (u, v, w) in G.edges(data=True):
    w['weight'] = random.randint(0, 10)

pos = nx.shell_layout(G)
# dibujo el grafo
printGraph(G, pos)
# Y MIREN! tienen la solucion secuencial del ejercicio para testear validez!
# igual usen el de catedra tambien
T = nx.minimum_spanning_tree(G)
printGraph(T, pos)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
