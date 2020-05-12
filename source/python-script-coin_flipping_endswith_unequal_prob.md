---
title: python script coin flipping endswith unequal prob (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'coin flipping endswith unequal prob'

Functions in program: 
* `def toss(s, p=0.5):`
* `def E_bottomup(x, p=0.5):`
* `def E_topdown(x, p=0.5, cache=None):`

Modules used in program: 
* `import random`

## python coin flipping endswith unequal prob

Python example: coin flipping endswith unequal prob

```python
import random
# E(x) = E(x[:-1]) + a + b(1 + E(x) - E(x[:max(xrange(len(x) - 1, -1, -1), key=lambda i:x[:i] == (x[:-1] + chr(ord(x[-1]) ^ ord('T') ^ ord('H')))[len(x) - i:])]))
# (1 - b)E(x) = E(x[:-1]) + a + b - bE(x[...])
# E(x) = (E(x[:-1]) + a + b - bE(x[...])) / (1 - b)

def E_topdown(x, p=0.5, cache=None):
    if cache is None:
        cache = {"": 0}
    if x in cache:
        return cache[x]
    if x[-1] == 'H':
        a, b = p, 1 - p
    else:
        a, b = 1 - p, p
    ret = (E_topdown(x[:-1], p, cache) + 1 - b * E_topdown(x[:max(xrange(len(x) - 1, -1, -1), key=lambda i:x[:i] == (x[:-1] + chr(ord(x[-1]) ^ ord('T') ^ ord('H')))[len(x) - i:])], p, cache)) / (1 - b)
    cache[x] = ret
    return ret

def E_bottomup(x, p=0.5):
    table = [0]
    for i in xrange(1, len(x) + 1):
        x_prefix = x[:i]

        if x_prefix[-1] == 'H':
            a, b = p, 1 - p
        else:
            a, b = 1 - p, p

        x_flip_tail = x_prefix[:-1] + chr(ord(x_prefix[-1]) ^ ord('T') ^ ord('H'))
        match_offset = next(offset for offset in range(len(x_prefix) - 1, -1, -1) if x_prefix[:offset] == x_flip_tail[len(x_prefix) - offset:])
        table.append((table[-1] + 1 - b * table[match_offset]) / (1 - b))
    return table[len(x)]

def toss(s, p=0.5):
    cnt = 0
    ary = [None] * len(s)
    while True:
        ary = ary[1:] + ['H' if random.random() < p else 'T']
        cnt += 1
        if ary == list(s):
            return cnt

for _ in xrange(100):
    l = random.randint(1, 10)
    s = ''.join(random.choice('HT') for _ in xrange(l))
    p = random.random()
    N = 100
    #t =  sum(toss(s, p) for i in xrange(N)) / float(N)
    dp = E_topdown(s, p)
    #print('%.2f' % ((t - dp) / dp * 100) + '%')
    #print
    print(s, p)
    print(dp)
    #print(t)
    assert abs(E_topdown(s, p) - E_bottomup(s, p)) < 1e-5


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
