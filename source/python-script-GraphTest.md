---
title: python script GraphTest (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'GraphTest'


Modules used in program: 
* `import string`

## python GraphTest

Python example: GraphTest

```python
import string

try:
    from Gui import Gui, GuiCanvas
except ImportError:
    from swampy.Gui import Gui, GuiCanvas

from Graph import Vertex
from Graph import Edge
from Graph import Graph
from GraphWorld import GraphWorld
from GraphWorld import CircleLayout
from GraphWorld import RandomLayout


if __name__ == '__main__':
  # create n Vertices
  n = 11
  labels = string.ascii_lowercase + string.ascii_uppercase
  vs = [Vertex(c) for c in labels[:n]]

  # create a graph and a layout
  g = Graph(vs)
  #g.add_all_edges()
  g.add_regular_edges(2)
  layout = CircleLayout(g)
  #layout = RandomLayout(g)

  # draw the graph
  gw = GraphWorld()
  gw.show_graph(g, layout)
  gw.mainloop()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
