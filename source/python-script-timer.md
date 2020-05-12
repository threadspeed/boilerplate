---
title: python script timer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'timer'

Functions in program: 
* `def test(r=3, times=400):`
* `def make_line_mod1(integer, step):`
* `def make_line_original(integer, step):`

## python timer

Python example: timer

```python
from timeit import Timer

setup = """\
from mathutils import Vector
from random import random
from itertools import zip_longest
from data_structure import fullList

def make_line_original(integer, step):
    vertices = [(0.0, 0.0, 0.0)]
    integer = [int(integer) if type(integer) is not list else int(integer[0])]

    if type(step) is not list:
        step = [step]
    fullList(step, integer[0])

    for i in range(integer[0]-1):
        v = Vector(vertices[i]) + Vector((step[i], 0.0, 0.0))
        vertices.append(v[:])

    edges = []
    for i in range(integer[0]-1):
        edges.append((i, i+1))

    return vertices, edges

def make_line_mod1(integer, step):
    integer = [int(integer) if type(integer) is not list else int(integer[0])]
    vertices = [(0,0,0)]
    vadd = vertices.append

    if type(step) is not list:
        step = [step]
    fullList(step, integer[0])

    component = 0.0
    for i in range(1, integer[0]):
        component += step[i]
        v = (component, 0.0, 0.0)
        vadd(v)

    edges = []
    for i in range(integer[0]-1):
        edges.append((i, i+1))

    return vertices, edges



"""


def test(r=3, times=400):
    command = """m = make_line_original(200, 0.2)"""
    t2 = Timer(command, setup=setup)
    print(command, min(t2.repeat(r, times)))

    command = """m = make_line_mod1(200, 0.2)"""
    t2 = Timer(command, setup=setup)
    print(command, min(t2.repeat(r, times)))


test()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
