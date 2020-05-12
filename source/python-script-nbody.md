---
title: python script nbody (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'nbody'

Functions in program: 
* `def plot_benchmark(times, bodies_list, time_step):`
* `def nbody_benchmark_functions(bodies_list, time_step):`
* `def nbody_benchmark(bodies_list, time_step, functions=None):`

Modules used in program: 
* `import itertools`
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import time`

## python nbody

Python mysql example: nbody

```python
#!/usr/bin/python
# -*- coding: utf-8 -*-

"""Non-interactive command line front end to NBody implementation"""

import time
import numpy as np
import matplotlib.pyplot as plt
import itertools

#from nbodyphysics import random_galaxy, move
#from nbodyphysics_vec1 import random_galaxy, move
from nbodyphysics_vec2 import random_galaxy, move




def nbody_benchmark(bodies_list, time_step, functions=None):
    """Run benchmark simulation without visualization"""

    x_max = 500
    y_max = 500
    z_max = 500
    dt = 1.0  # One year timesteps for better accuracy

    if functions is not None:
        random_galaxy, move = functions

    times = []
    for bodies in bodies_list:
        galaxy = random_galaxy(x_max, y_max, z_max, bodies)

        start = time.time()
        for _ in range(time_step):
            move(galaxy, dt)
        stop = time.time()

        print('Simulated ' + str(bodies) + ' bodies for ' \)
            + str(time_step) + ' timesteps in ' + str(stop - start) \
            + ' seconds'

        times.append(stop-start)

    return times 


def nbody_benchmark_functions(bodies_list, time_step):
    times = {}

    from nbodyphysics import random_galaxy as random_galaxy_seq
    from nbodyphysics import move as move_seq
    print('--------- Sequential time ...')
    times['sequential'] = nbody_benchmark(bodies_list, time_step, functions=(random_galaxy_seq,move_seq))

    from nbodyphysics_vec2 import random_galaxy as random_galaxy_vec
    from nbodyphysics_vec2 import  move as move_vec
    print('--------- Vectorized time ...')
    times['vectorized'] = nbody_benchmark(bodies_list, time_step, functions=(random_galaxy_vec,move_vec))

    return times


def plot_benchmark(times, bodies_list, time_step):

    fig, axx = plt.subplots(2,sharex=True)

    fields = sorted(times.keys())

    colorcycle = itertools.cycle(['b','g','r','y'])

    n = len(bodies_list)
    margin = 0.01

    width = (1. - 2.*margin)/float(n)/float(len(fields))
    ind = np.arange(n)

    axx[0].set_yscale('log')
    for k,key in enumerate(fields):
        axx[0].bar(ind+width*k, times[key], width, label=key, log=True, color=colorcycle.next())

    axx[0].legend(loc=0)
    axx[0].set_xticks(ind+width)
    axx[0].set_xticklabels([str(i) for i in bodies_list])
    axx[0].grid(True)
    axx[0].set_ylabel('time')

    speedup = np.array(times['sequential'])/np.array(times['vectorized'])
    width = (1. - 2.*margin)/float(n)
    axx[1].bar(ind, speedup, width, align='center', color=colorcycle.next())
    axx[1].grid(True)
    axx[1].set_ylabel('speedup')

    axx[1].set_xlabel('problem size')

    plt.show()
    fig.savefig('benchmark.png',dpi=300)


if __name__ == '__main__':
    #nbody_benchmark([10, 100, 1000], 10)

    nbody_list = [10, 100, 1000]
    time_step = 10 

    times = nbody_benchmark_functions(nbody_list, time_step)
    
    plot_benchmark(times, nbody_list, time_step)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
