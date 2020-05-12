---
title: python script CS166 9-1 SIS infection (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'CS166 9-1 SIS infection'

Functions in program: 
* `def set_n(val = n):`
* `def set_p_r(val = p_r):`
* `def set_p_i(val = p_i):`
* `def set_p_e(val = p_e):`
* `def update():`
* `def update_asynchoronous():`
* `def update_synchronous():`
* `def observe():`
* `def initialize():`

Modules used in program: 
* `import pycxsimulator`
* `import sys`
* `import random as rd`
* `import networkx as nx`
* `import matplotlib`

## python CS166 9-1 SIS infection

Python mysql example: CS166 9-1 SIS infection

```python
import matplotlib
matplotlib.use('TkAgg')
from pylab import *
import networkx as nx
import random as rd
import sys

p_e = 0.1 # Proability of connection
p_i = 0.5 # infection probability
p_r = 0.5 # recovery probability
n = 100

if len(sys.argv) > 1:
    update_mode = sys.argv[1]    
else:
    update_mode = 'synchronous'

# Modify Code 16.6 to implement a synchronous, simultaneous up- dating version of the network SIS model. Then simulate its dynamics on an Erdo ̋s- Re ́nyi random network for the following parameter settings:
# • n=100,pe =0.1,pi =0.5,pr =0.5(pr <(n−1)pepi) 
# • n=100,pe =0.1,pi =0.04,pr =0.5(pr >(n−1)pepi) 
# • n=200,pe =0.1,pi =0.04,pr =0.5(pr <(n−1)pepi) 
# * n=200,pe =0.05,pi =0.04,pr =0.5(pr >(n−1)pepi)
# Discuss how the results compare to the predictions made by the mean-field ap- proximation.

# Compare synchronous and asynchronous update

def initialize():
    global g
    g = nx.erdos_renyi_graph(n, p_e)
    g.pos = nx.spring_layout(g)
    for i in g.nodes:
        g.nodes[i]['state'] = 1 if random() < p_i else 0

def observe():
    global g
    cla()
    g.pos = nx.spring_layout(g)
    nx.draw(g, vmin = 0, vmax = 1,
            node_color = [g.nodes[i]['state'] for i in g.nodes],
            pos = g.pos)


def update_synchronous():
    global g
    next_g = g.copy()
    for a in list(g.nodes):
        if g.nodes[a]['state'] == 0: # if susceptible
            for b in list(next_g.neighbors(a)):
                if g.nodes[b]['state'] == 1: # if neighbor b is infected
                    next_g.nodes[a]['state'] = 1 if random() < p_i else 0
        else: # if infected
            next_g.nodes[a]['state'] = 0 if random() < p_r else 1
    g = next_g

def update_asynchoronous():
    global g
    a = rd.choice(list(g.nodes))
    if g.nodes[a]['state'] == 0: # if susceptible
        b = rd.choice(list(g.neighbors(a)))
        if g.nodes[b]['state'] == 1: # if neighbor b is infected
            g.nodes[a]['state'] = 1 if random() < p_i else 0
    else: # if infected
        g.nodes[a]['state'] = 0 if random() < p_r else 1

def update():
    if update_mode == 'synchronous':
        update_synchronous()
    else:
        update_asynchoronous()

def set_p_e(val = p_e):
    global p_e
    p_e = float(val)
    return val

def set_p_i(val = p_i):
    global p_i
    p_i = float(val)
    return val

def set_p_r(val = p_r):
    global p_r
    p_r = float(val)
    return val

def set_n(val = n):
    global n
    n = int(val)
    return val


print(update_mode)
import pycxsimulator

pycxsimulator.GUI(parameterSetters=[set_p_e, set_p_i, set_p_r, set_n]).start(func=[initialize, observe, update])




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
