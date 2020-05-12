---
title: python script ondemand scheduler (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ondemand scheduler'

Functions in program: 
* `def work(i):`

Modules used in program: 
* `import random`
* `import time`

## python ondemand scheduler

Python example: ondemand scheduler

```python
from IPython.parallel import Client
from IPython.parallel import interactive
import time
import random

@interactive
def work(i):
    import time
    import random
    sleeptime = 1 + random.random() * 2
    time.sleep(sleeptime)
    return i, sleeptime

client = Client()

dv = client.direct_view()

promises = []
results = []

submit_idx = 0
t0 = time.time()
while True:
    qstatus = client.queue_status()
    del qstatus['unassigned']
    for eid, estatus in qstatus.items():
        if estatus['queue'] == 0:
            print('generate some work for', eid)
            promises.append(
                dv._really_apply(
                    work,
                    args=(submit_idx,),
                    targets=[eid]))
            submit_idx += 1
    # do like this to avoid race conditions
    new_promises = []
    for p in promises:
        if p.ready():
            results.append(p.get()[0])
        else:
            new_promises.append(p)
    promises = new_promises
    print('n engines', len(client),)
    print('total time: ', (time.time() - t0),)
    if results:
        print('time spent in workers', sum(zip(*results)[1]))
    else:
        print
    time.sleep(.5)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
