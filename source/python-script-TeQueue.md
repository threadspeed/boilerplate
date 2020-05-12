---
title: python script TeQueue (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'TeQueue'

Functions in program: 
* `def tepop(l, d):`
* `def tepush(l, d, m, sortkey, value):`

Modules used in program: 
* `import heapq`

## python TeQueue

Python mysql example: TeQueue

```python
import heapq
def tepush(l, d, m, sortkey, value):
    if not value in d:
        generation = 1
    else:
        generation = d[value] + 1
    d[value] = generation
    heapq.heappush(l, (sortkey, value, generation))
    length = len(l)
    if length > m: # ヒープの再構成
        lt = []
        for n in range(0,length):
            if l[n][2] == d[l[n][1]]:
                heapq.heappush(lt, (l[n][0], l[n][1], 1))
                d[l[n][1]] = 1
        return lt
    else:
        return l

def tepop(l, d):
    while len(l) > 0:
        (sortkey, value, generation) = heapq.heappop(l)
        if d[value] == generation:
            return (sortkey, value, generation) 


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
