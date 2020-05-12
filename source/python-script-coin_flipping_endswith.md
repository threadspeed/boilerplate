---
title: python script coin flipping endswith (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'coin flipping endswith'

Functions in program: 
* `def toss(s):`
* `def E_bottomup(x):`
* `def E_topdown(x, cache={'': 0}):`

Modules used in program: 
* `import random`

## python coin flipping endswith

Python mysql example: coin flipping endswith

```python
import random
# E(H) = E(T) = 2

# E(HT) = E(TH) = 4
# E(HH) = E(TT) = 6

# E(HHT) = E(TTH) = 8 (E(HH) + 1/2 + 1/2(1 + E(HHT) - E(HH))
# E(THH) = E(HTT) = 8 (E(TH) + 1/2 + 1/2(1 + E(THH) - E(T))
# E(HTH) = E(THT) = 10 (E(HT) + 1/2 + 1/2(1 + E(HTH)))
# E(HHH) = E(TTT) = 14 (E(HH) + 1/2 + 1/2(1 + E(HHH)))

# E(HHHH) = E(TTTT) = 30 (E(HHH) + 1/2 + 1/2(1 + E(HHHH)))
# E(HHHT) = E(TTTH) = 16 (E(HHH) + 1/2 + 1/2(1 + E(HHHT) - E(HHH)))
# E(HHTH) = E(TTHT) = 18 (E(HHT) + 1/2 + 1/2(1 + E(HHTH)))
# E(HHTT) = E(TTHH) = 16 (E(HHT) + 1/2 + 1/2(1 + E(HHTT) - E(H)))
# E(x) = E(x[:-1]) + 1/2 + 1/2(1 + E(x) - E(x[:max(xrange(len(x) - 1, -1, -1), key=lambda i:x[:i] == (x[:-1] + chr(ord(x[-1]) ^ ord('T') ^ ord('H')))[len(x) - i:])]))

def E_topdown(x, cache={'': 0}):
    global g_cache
    g_cache = cache
    if x in cache:
        return cache[x]
    ret = 2 * E_topdown(x[:-1]) + 2 - E_topdown(x[:max(xrange(len(x) - 1, -1, -1), key=lambda i:x[:i] == (x[:-1] + chr(ord(x[-1]) ^ ord('T') ^ ord('H')))[len(x) - i:])])
    cache[x] = ret
    return ret

def E_bottomup(x):
    table = [0]
    for i in xrange(1, len(x) + 1):
        x_prefix = x[:i]
        x_flip_tail = x_prefix[:-1] + chr(ord(x_prefix[-1]) ^ ord('T') ^ ord('H'))
        match_offset = next(offset for offset in range(len(x_prefix) - 1, -1, -1) if x_prefix[:offset] == x_flip_tail[len(x_prefix) - offset:])
        table.append(2 * table[-1] + 2 - table[match_offset])
    return table[len(x)]

def toss(s):
    cnt = 0
    ary = [None] * len(s)
    while True:
        ary = ary[1:] + [random.choice('HT')]
        cnt += 1
        if ary == list(s):
            return cnt

for _ in xrange(100):
    s = ''.join(random.choice('HT') for _ in xrange(5))
    N = 10000
    print(sum(toss(s) for i in xrange(N)) / float(N))
    print(E_topdown(s))
    assert E_topdown(s) == E_bottomup(s)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
