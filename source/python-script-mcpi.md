---
title: python script mcpi (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mcpi'

Functions in program: 
* `def estimate_pi_ipython(N_groups, N_per_group):`
* `def estimate_pi_list_comprehension(N):`
* `def estimate_pi_naive(N):`
* `def estimate_pi_celery(N_groups, N_per_group):`
* `def process_results(inside, total):`
* `def try_points(N):`
* `def _try_points(N):`
* `def try_point(point):`
* `def timeit(func):`

Modules used in program: 
* `import numpy as np`
* `import json`
* `import time`

## python mcpi

Python mysql example: mcpi

```python
"""Comparison of Monte Carlo calculations of pi using different
methods of parallelism (or lack thereof).

To run, this requires the following Python packages:

* redis
* celery
* numpy

To run the celery implementation, you will need to have a Redis server
installed on your local machine. To run the celery workers, use the
command::

  $ celery worker -A mcpi

This will default to using N worker processes, where N is the number
of CPU cores on your machine.

For the IPython parallel implementation, you need to run the ipcluster
command::

  $ ipcluster start

As with the celery case, this will by default start as many processes
as available CPU cores.

"""

import time
import json
import numpy as np
from numpy.random import random
from celery import Celery, chord
from IPython import parallel

app = Celery('mcpi', broker='redis://', backend='redis://')

times = {}

def timeit(func):
    """Decorator for timing how long a function takes."""
    def wrapped(*args, **kwargs):
        t_start = time.time()
        result = func(*args, **kwargs)
        t_total = time.time() - t_start
        print('Execution time: {:.3f} s'.format(t_total))
        if func.__name__ in times:
            times[func.__name__].append(t_total)
        else:
            times[func.__name__] = [t_total]
        with open('times.json', 'w') as outfile:
            outfile.write(json.dumps(times))
        return result
    return wrapped

def try_point(point):
    """Throws a single dart and returns 1 if inside the target region,
    else 0.

    """
    x, y = point
    if x**2 + y**2 < 1:
        return 1.
    else:
        return 0.

def _try_points(N):
    """Throws N darts and returns the number that landed inside the
    target region. Separated from the celery task in order to work
    more easily with IPython's parallel model.

    """
    points = random((N, 2))
    inside = 0.
    for point in points:
        inside += try_point(point)
    return inside

@app.task
def try_points(N):
    """Wraps _try_points for celery."""
    return _try_points(N)

@app.task
def process_results(inside, total):
    """Estimates pi given the number of darts that landed inside the
    target region and the total number of darts thrown.

    """
    if isinstance(inside, list):
        inside = np.sum(inside)
    return 4*inside/total

@timeit
def estimate_pi_celery(N_groups, N_per_group):
    """Estimate pi using celery. Monte Carlo tries are grouped in
    N_groups groups of size N_per_group.

    """
    print("Starting with celery...")
    res = chord(
        (try_points.s(N_per_group) for N in range(N_groups)),
        process_results.s(N_groups*N_per_group))()
    pi = res.get()
    print("pi is approximately", pi)

@timeit
def estimate_pi_naive(N):
    """Naively estimate pi."""
    print("Starting with naive single-threaded Python...")
    inside = 0
    for _ in range(N):
        inside += try_point(random((2,)))
    inside = np.sum(inside)
    print("pi is approximately", process_results(inside, N))

@timeit
def estimate_pi_list_comprehension(N):
    """Use list comprehension and numpy to estimate pi. This should be
    significantly faster than the naive approach.

    """
    print("Starting with list comprehension and numpy...")
    inside = np.sum([try_point(point) for point in random((N, 2))])
    print("pi is approximately", process_results(inside, N))

@timeit
def estimate_pi_ipython(N_groups, N_per_group):
    """The same as the celery example, but using IPython's parallel
    computing model.

    """
    print("Starting with IPython parallel cluster...")
    client = parallel.Client()
    client[:].execute('from numpy.random import random')
    client[:]['try_point'] = try_point
    mapped = client[:].map(_try_points, [N_per_group for N in range(N_groups)])
    while not mapped.ready():
        pass
    print("pi is approximtaely", process_results(mapped.get(), N_groups*N_per_group))

if __name__ == "__main__":
    N_groups = 1000
    N_per_group = 10000
    for _ in range(50):
        estimate_pi_celery(N_groups, N_per_group)
        print()
        estimate_pi_naive(N_groups*N_per_group)
        print()
        estimate_pi_list_comprehension(N_groups*N_per_group)
        print()
        estimate_pi_ipython(N_groups, N_per_group)
    

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
