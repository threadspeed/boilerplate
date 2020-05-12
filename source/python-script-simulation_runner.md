---
title: python script simulation runner (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'simulation runner'

Functions in program: 
* `def bubble_expand(good_bubbles):`
* `def initalize_experiment(n, p, g):`
* `def generate_random_bubble_graph(n, p):`

Modules used in program: 
* `import random`

## python simulation runner

Python example: simulation runner

```python
from bubble_expand import Bubble
from bubble_simulation import Test
from base_bubble_tools import bernoulli_sample, create_undirected_edge

import random


def generate_random_bubble_graph(n, p):
    """
    n -- number of nodes in the graph
    p -- probability that an edge exists between any two given pair of nodes
    """
    graph = []
    for i in range(n):
        this_bubble = Bubble("Bubble "+str(i+1), 0)
        for prev_bubbles in graph:
            if bernoulli_sample(p):
                create_undirected_edge(this_bubble, prev_bubbles)
        graph.append(this_bubble)
    return graph

    

def initalize_experiment(n, p, g):
    """
    n -- number of nodes / interests
    p -- prob of edge
    g -- number of good bubbles to pick
    """
    a_graph = generate_random_bubble_graph(n, p)
    return random.sample(a_graph, g), a_graph
        

def bubble_expand(good_bubbles):
    """
    good_bubbles -- a list of good bubbles
    """
    candidates = []
    for good_bubble in good_bubbles:
        for bubble in good_bubble.neighbors:
            if bubble not in good_bubbles:
                candidates.append(bubble)

    good_candidates = []
    for candidate in candidates:
        current_test = Test(candidate)
        current_test.simulate_n(100, .01)
        if current_test.is_success(1):
            good_candidates.append(candidate)
    return good_candidates


if __name__ == "__main__":
    good_bubbles, random_bubble_graph = initalize_experiment(10, .2, 1)
    print("Starting good bubbles")
    print([x.name for x in good_bubbles])
    for i in range(10):
        print("-------------------------------------")
        print("ROUND " + str(i+1))
        new_good_bubbles = bubble_expand(good_bubbles)
        print("Added these bubbles to good bubbles")
        print([x.name for x in new_good_bubbles])
        good_bubbles.extend(new_good_bubbles)
    print("-------------------------------------")
    print("Final Good Bubbles")
    print([x.name for x in good_bubbles])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
