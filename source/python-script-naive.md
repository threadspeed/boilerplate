---
title: python script naive (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'naive'

Functions in program: 
* `def gen(term, sz):`
* `def get_signature(expr, points):`
* `def evaluate(expr, values):`

Modules used in program: 
* `import random`
* `import itertools`

## python naive

Python mysql example: naive

```python
import itertools
import random

gram = {
    "T": [
        ["0"],
        ["1"],
        ["x"],
        ["y"],
        ["+", "T", "T"],
        ["-", "T", "T"],
        ["<", "T", "T"],
        ["=", "T", "T"],
        ["ite", "T", "T", "T"],
    ]
}

def evaluate(expr, values):
    name = expr[0]
    rest = expr[1:]
    if name == "0": return 0
    elif name == "1": return 1
    elif name == "x": return values["x"]
    elif name == "y": return values["y"]
    elif name == "-":
        return evaluate(rest[0], values) - evaluate(rest[1], values)
    elif name == "+":
        return evaluate(rest[0], values) - evaluate(rest[1], values)
    elif name == "=":
        return evaluate(rest[0], values) == evaluate(rest[1], values)
    elif name == "<":
        return evaluate(rest[0], values) < evaluate(rest[1], values)
    elif name == "ite":
        if evaluate(rest[0], values):
            return evaluate(rest[1], values)
        else:
            return evaluate(rest[2], values)

def get_signature(expr, points):
    res = []
    for values in points:
        res.append(evaluate(expr, values))
    return tuple(res)

def gen(term, sz):
    #print("gen", term, sz)
    if term not in gram:
        if sz == 1:
            yield term
        return

    for poss in gram[term]:
        if len(poss) > sz: continue
        parts = {}
        for sub in poss:
            for subsz in range(0, sz+2-len(poss)):
                g = gen(sub, subsz)
                parts[(sub, subsz)] = [_ for _ in g]

        #print(parts)

        for sizes in itertools.product(range(0, sz+2-len(poss)), repeat=len(poss)):
            if sum(sizes) != sz: continue
            subposs = [parts[(p, s)] for p,s in zip(poss, sizes)]
            #print(poss, sizes, subposs)
            for it in itertools.product(*subposs):
                #print("it", it)
                yield it

points = []
expected = []
N = 12
for i in range(N*N):
    x = i / N
    y = i % N
    points.append({"x": x, "y": y})
    expected.append(min(x, y))

expected = tuple(expected)


for sz in range(10):
    g = gen("T", sz)
    good = []
    mx = 0
    distinct = set()
    for i, _ in enumerate(g):
        sign = get_signature(_, points)
        if sign == expected:
            good.append(_)
        distinct.add(sign)

        mx = i + 1

    print(mx, "options considered at size", sz)
    print(len(distinct), "distinct")
    print(len(good), "are good")

    if good:
        print("- like:", good[0])



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
