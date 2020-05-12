---
title: python script Tiezzi 5992531 Es7 test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Tiezzi 5992531 Es7 test'

Functions in program: 
* `def testC():`
* `def testB():`
* `def testA():`

Modules used in program: 
* `import random`

## python Tiezzi 5992531 Es7 test

Python example: Tiezzi 5992531 Es7 test

```python
from Graph import Graph
from matplotlib import pyplot as plt
import random


def testA():
    numeroSCC = []
    for i in range(1, 2000):
        gr = Graph(1000)
        gr.ShuffleEdge(i)
        numeroSCC.append(gr.printSCCs())
    plt.plot(numeroSCC, label="#SCC all'aumentare della percentuale di archi, grafo dimensione fissa.")
    plt.legend()
    plt.show()


def testB():
    i = 1
    numeroSCC = []
    while i < 1000:
        g = Graph(i)
        g.ShuffleEdge(100)
        numeroSCC.append(g.printSCCs())
        i += 1
    plt.plot(numeroSCC, label="#SCC all'aumentare della dimensione del grafo con percentuale archi del 100%.")
    plt.legend()
    plt.show()


def testC():
    i = 1
    numeroSCC = []
    while i < 1000:
        g = Graph(i)
        for j in range(0, 500):
            g.addEdge(random.randint(0, i - 1), random.randint(0, i - 1))
        numeroSCC.append(g.printSCCs())
        i += 1
    plt.plot(numeroSCC, label="#SCC all'aumentare della dimensione del grafo con numero di archi fisso")
    plt.legend()
    plt.show()

# testC()
#testA()
testB()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
