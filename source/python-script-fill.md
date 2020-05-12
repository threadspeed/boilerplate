---
title: python script fill (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'fill'

Functions in program: 
* `def customfill_():`

Modules used in program: 
* `import stratify`
* `import sys`
* `import random`
* `import itertools`

## python fill

Python mysql example: fill

```python
#!/usr/local/bin/python3.3 -tt

import itertools
import random
import sys

import stratify


def customfill_():
    # customfill function fills the empty cells as depiced below:
    #
    #   000 000 007 000 500 010 900 000 00
    #                   :
    #   9BB 5BB B17 9BB 5BB B17 9BB 5BB B1
    #
    def _(iterable, offset=None):
        nonlocal g

        pool = list(iterable)

        size = len(pool)

        if size >= 9:
            phase = [0] * 9

            for i in range(size):
                if pool[i] != 0:
                    phase[i % 9] = pool[i]

            if any(i == 0 for i in phase):
                c = next(g)
                for i in range(9):
                    if phase[i] == 0:
                        phase[i] = c

            for i in range(size):
                pool[i] = phase[i % 9]

        # Assertion to ensure phase consistency
        if True:
            for i in range(size):
                for j in range(i, size, 9):
                    assert(pool[i] == pool[j])

        return pool

    g = itertools.cycle(('ABCDEFGHIJKLMNOPQRSTUVWXYZ'
                         'abcdefghijklmnopqrstuvwxyz'))

    return _

customfill = customfill_()


if __name__ == '__main__':
    random.seed(0)

    a = []
    for l in sys.stdin:
        a.append([])
        for i in l.split():
            a[-1].append(int(i));

    h, w = len(a), len(a[0])

    for i in range(h):
        v = stratify.stratify(a[i], customfill)

        print(' '.join(str(_) for _ in v))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
