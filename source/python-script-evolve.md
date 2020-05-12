---
title: python script evolve (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'evolve'

Functions in program: 
* `def main():`

Modules used in program: 
* `import random`

## python evolve

Python mysql example: evolve

```python
#!/usr/bin/env python3

import random
from collections import Counter

from organism import Organism
from allowed_blocks import *

def main():
    # generations = []
    generation = 0
    values = []
    length = 100
    keep = 60

    orgs = [Organism(reactor_size = (5, 5, 5), mutability = 0.01, allowed_blocks = easy_blocks) for i in range(length)]
    while True:
        values = [org.fitness() for org in orgs]
        # generations.append((max(orgs, key=lambda org: org.fitness()).chromosome.encoded_data(), max(values), sum(values)/float(len(values))))
        print(max(orgs, key=lambda org: org.fitness()), max(values), sum(values)/float(len(values)))

        # Species Distribution:
        print(Counter((org.pretty_size for org in orgs)).most_common(7))

        orgs.sort(key = lambda org: org.fitness(), reverse = True)
        orgs = orgs[:keep]
        for i in range(length - keep):
            orgs.append(Organism(parent = orgs[i % keep]))
        if generation % 100 == 0:
            for org in orgs[keep:]:
                org.mutate(0.1)
        elif generation % 20 == 0:
            for org in orgs[keep:]:
                org.mutate(0.05)
        else:
            for org in orgs[keep:]:
                org.mutate()

        generation += 1


if __name__ == "__main__":
    main()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
