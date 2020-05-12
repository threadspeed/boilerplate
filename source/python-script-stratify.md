---
title: python script stratify (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'stratify'

Functions in program: 
* `def stratify(iterable, filler=defaultfill, verbose=False):`
* `def dfs(v, padding=0, cont=None):`
* `def compose(a):`
* `def defaultfill(iterable, offset=None):`

Modules used in program: 
* `import score`
* `import fill`
* `import sys`
* `import random`
* `import operator`
* `import itertools`

## python stratify

Python example: stratify

```python
#!/usr/local/bin/python3.3 -tt

import itertools
import operator
import random
import sys

import fill
import score


INFTY = 1e+9


def defaultfill(iterable, offset=None):
    # defaultfill function fills empty cells as depicted below:
    #
    #   105 002 000 105 0
    #           :
    #   165 932 748 165 9
    #
    pool = list(iterable)

    size = len(pool)

    phase = [-1] * 10

    for i in range(size):
        if pool[i] != 0:
            phase[pool[i]] = i % 9

    for i in range(1, 9+1):
        if phase[i] >= 0:
            for j in range(phase[i], size, 9):
                pool[j] = i

    rest = [i for i in range(1, 9+1) if phase[i] == -1]

    random.shuffle(rest)

    g = itertools.cycle(rest)

    for i in range(size):
        if pool[i] == 0:
            pool[i] = next(g)

    # Assertion to ensure phase consistency
    if True:
        for i in range(size):
            for j in range(i, size, 9):
                assert(pool[i] == pool[j])

    return pool

def compose(a):
    h, w = len(a), len(a[0])

    # Note that elements of dp holds vector pointing to the source
    # that contributes highest score.
    dp = [[[0, 0, 0] for i in range(w+1)] for j in range(h+1)]

    # l and u holds range of interest to accelerate the whole process.
    u = 0

    for i in range(h):
        for j in range(w):
            l = j
            if a[i][j]:
                break

        for j in range(w, 0, -1):
            uu = j
            if a[i][j-1]:
                break

        if uu > u:
            u = uu

        for j in range(w):
            if j < l:
                continue
            for k in range(j, w+1):
                if k > u:
                    break
                s = dp[i][j][0] + max((k - j - 9 + 1, 0))
                if s > dp[i+1][k][0]:
                    dp[i+1][k] = s, i, j

    if False:
        for i in dp:
            print('stratify.compose:', ' '.join('%3d' % t[0] for t in i), file=sys.stderr)

    # Find highest score to retrieve path.
    sp, y, x = 0, 0, 0

    for i in range(h+1):
        for j in range(w+1):
            if dp[i][j][0] > sp:
                y, x, sp = i, j, dp[i][j][0]

    # Reconstruct solution by the backward tracing.
    vv = [0] * w

    while x:
        yy, xx = dp[y][x][1:]

        if False:
            print(x, y, xx, yy, a[yy][xx:x])

        if x - xx - 1 >= 9:
            for i in range(xx, x):
                vv[i] = a[yy][i]

        y, x = yy, xx

    return vv

def dfs(v, padding=0, cont=None):
    size = len(v)

    # Stratify by surrounding cells
    for i in range(size):
        if v[i] != 0:
            for j in range(1, 8+1):
                if i + j < size:
                    if v[i + j] == v[i]:
                        a, b = v[:i+j], v[i+1:]
                        dfs(a, padding,         cont)
                        dfs(b, padding + i + 1, cont)
                        return

    # Stratify by phase conflict
    t = (INFTY, )

    for i in range(size):
        if v[i] != 0:
            for j in range(i+9, size, 9):
                if v[j] != 0:
                    if v[j] != v[i]:
                        d = j - i
                        if d < t[0]:
                            t = (d, i, j)

    if t[0] < INFTY:
        i, j = t[1:]
        a, b = v[:j], v[i+1:]
        dfs(a, padding,         cont)
        dfs(b, padding + i + 1, cont)
        return

    # Stratify by multi phase
    t = (INFTY, )

    for i in range(size):
        if v[i] != 0:
            for j in range(i+1, size):
                if v[j] != 0:
                    if j % 9 != i % 9:
                        if v[j] == v[i]:
                            d = j - i
                            if d < t[0]:
                                t = (d, i, j)

    if t[0] < INFTY:
        i, j = t[1:]
        a, b = v[:j], v[i+1:]
        dfs(a, padding,         cont)
        dfs(b, padding + i + 1, cont)
        return

    # Pass the result to the continuous function.
    if cont:
        cont(v, padding)

def stratify(iterable, filler=defaultfill, verbose=False):
    def _(v, padding):
        v = filler(v, padding)

        vv = [0] * len(pool)

        for i in range(len(v)):
            vv[i + padding] = v[i]

        m.append(vv)

    pool = tuple(iterable)

    m = []

    dfs(pool, cont=_)

    m.sort(key=lambda x: len(tuple(itertools.takewhile(operator.not_, x))))

    v = compose(m)

    # Impterpolate resulting vector with predetermined cells.
    for i in range(len(pool)):
        if v[i] == 0:
            v[i] = pool[i]
    
    if verbose or False:
        print('input:  <', ''.join(str(_) for _ in pool), file=sys.stderr)

        for i in m:
            print('strata: .', ''.join(str(_) for _ in i), file=sys.stderr)

        print('result: >', ''.join(str(_) for _ in v), file=sys.stderr)

        print(file=sys.stderr)

    return v

            
if __name__ == '__main__':
    if True:
        def customfill(iterable, offset=None):
            pool = list(iterable)

            size = len(pool)

            phase = [0] * 9

            for i in range(size):
                if pool[i] != 0:
                    phase[i % 9] = pool[i]

            for i in range(9):
                if phase[i] == 0:
                    phase[i] = '.'

            for i in range(size):
                pool[i] = phase[i % 9]

            # Assertion to ensure phase consistency
            if True:
                for i in range(size):
                    for j in range(i, size, 9):
                        assert(pool[i] == pool[j])

            return pool

        # Passing the following vector to stratify function with the
        # above customfill function results like:
        #
        #   input:  < 0909000050000000070005000109000000040000000000000000003002900030
        #   strata: . .9.0000000000000000000000000000000000000000000000000000000000000
        #   strata: . 00.9....5...9....00000000000000000000000000000000000000000000000
        #   strata: . 0000000009..5...179..5...179..5...100000000000000000000000000000
        #   strata: . 0000000000000000009..5...149..5...149..5...149..5...140000000000
        #   strata: . 0000000000000000000000000000..29...43..29...43..29...43..29...00
        #   strata: . 0000000000000000000000000000000000000000000000000000000..29...3.
        #   result: > 0909000059..5...179..5...179..29...43..29...43..29...43..29...30
        #
        #  By default, empty cells will be filled by defaultfill using
        #  randomize algorithm like:
        #
        #   input:  < 0909000050000000070005000109000000040000000000000000003002900030
        #   strata: . 6940000000000000000000000000000000000000000000000000000000000000
        #   strata: . 0079438251679438200000000000000000000000000000000000000000000000
        #   strata: . 0000000009325468179325468179325468100000000000000000000000000000
        #   strata: . 0000000000000000009865327149865327149865327149865327140000000000
        #   strata: . 0000000000000000000000000000752916843752916843752916843752916800
        #   strata: . 0000000000000000000000000000000000000000000000000000000682917435
        #   result: > 0909000059325468179325468179752916843752916843752916843752916830
        #

        v = '0909000050000000070005000109000000040000000000000000003002900030'
        
        stratify((int(_) for _ in v), filler=defaultfill, verbose=True)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
