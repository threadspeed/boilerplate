---
title: python script pushtest (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pushtest'


Modules used in program: 
* `import datetime`
* `import heapq`
* `import Queue`

## python pushtest

Python example: pushtest

```python
import Queue
import heapq
import datetime

d = datetime.datetime(1,1,1)
time1 = d.now()
t = Queue.PriorityQueue(N)
for n in range(0,N):
    t.put((target[n], n))
time2 = d.now()
u = []
for n in range(0,N):
    heapq.heappush(u, (target[n], n))
time3 = d.now()
v = []
dd = {}
for n in range(0,N):
    v = tepush(v, dd, 2*M, target[n], n)
time4 = d.now()
print('push:Queue',(time2 - time1).__str__())
print('push:Heap',(time3 - time2).__str__())
print('push:TeQ',(time4 - time3).__str__())


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
