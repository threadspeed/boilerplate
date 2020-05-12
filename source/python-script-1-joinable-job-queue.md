---
title: python script 1-joinable-job-queue (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '1-joinable-job-queue'

Functions in program: 
* `def boss():`
* `def worker(name):`
* `def job(job_id, worker):`

Modules used in program: 
* `import functools`
* `import gevent.queue`
* `import random`
* `import gevent`
* `import time`

## python 1-joinable-job-queue

Python example: 1-joinable-job-queue

```python
#import Queue
import time
import gevent
import random
import gevent.queue
import functools


#tasks = gevent.queue.Queue()
tasks = gevent.queue.JoinableQueue()


def job(job_id, worker):
    print("[{}]job {} process".format(worker, job_id))
    for i in range(0, random.randint(0, 100)):
        if worker == 'worker-01':
            gevent.sleep(0.1)
        else:
            gevent.sleep(0.01)

def worker(name):
    while not tasks.empty():
        task = tasks.get()
        print('[{}] got task {}'.format(name, task))
        task(worker=name)
        tasks.task_done()
    print('[{}]quitting time!'.format(name))

def boss():
    for i in xrange(1, 100):
        tasks.put_nowait(functools.partial(job, job_id=i))
    tasks.join()
    print("[boss]tasks finish")

gevent.spawn(boss)
gevent.joinall([
    gevent.spawn(worker, 'worker-01'),
    gevent.spawn(worker, 'worker-02'),
    gevent.spawn(worker, 'worker-03'),
])

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
