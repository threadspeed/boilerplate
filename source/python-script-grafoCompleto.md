---
title: python script grafoCompleto (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'grafoCompleto'


Modules used in program: 
* `import random`
* `import networkx as nx`

## python grafoCompleto

Python example: grafoCompleto

```python
#!/usr/bin/python3
# -*- coding: utf-8 -*-

import networkx as nx
import random

n = 5
# Creo un grafo completo
G = nx.complete_graph(n)
for (u, v, w) in G.edges(data=True):
    w['weight'] = random.randint(0, 10)

m = G.number_of_edges()
tamanios = "{}\n{}\n".format(n, m)
tamaniosBytes = bytes(tamanios, "utf-8")
with open("output.txt", "wb") as file:  # te hace el open y el close
    file.write(tamaniosBytes)
    nx.write_weighted_edgelist(G, file)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
