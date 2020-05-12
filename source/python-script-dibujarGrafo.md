---
title: python script dibujarGrafo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dibujarGrafo'


Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import random`
* `import networkx as nx`

## python dibujarGrafo

Python example: dibujarGrafo

```python
#!/usr/bin/python3
# -*- coding: utf-8 -*-

import networkx as nx
import random
import matplotlib.pyplot as plt

# grafo de n nodos donde la probabilidad de que un eje exista es de p
n = 5
G = nx.complete_graph(n)
for (u, v, w) in G.edges(data=True):
    w['weight'] = random.randint(0, 10)

edge_labels = nx.get_edge_attributes(G, 'weight')
label = nx.nodes(G)
nx.draw_shell(G, with_labels=True, edge_labels=edge_labels)
plt.show()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
