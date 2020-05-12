---
title: python script indexing time (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'indexing time'

Functions in program: 
* `def numpy_test():`
* `def python_list_test():`
* `def python_dict_test():`

Modules used in program: 
* `import numpy as np, numpy.random as rnd`
* `import itertools`
* `import random`
* `import timeit`

## python indexing time

Python example: indexing time

```python
import timeit
import random

import itertools

import numpy as np, numpy.random as rnd

num_states = 200000
num_actions = 10

def python_dict_test():

    # here's our q table, initialized with all possible state, action pairs
    dict_q = {}
    all_states = ( ("%s,%s" % x ) for x in itertools.product( range(num_states), range(num_actions)) )
    dict_q = dict.fromkeys(all_states, 0.0 )

    for i in range(num_states * num_actions):

        # use a random lookup sequence - this isn't a close approximation to how
        
        state = random.randint(0, num_states-1)
        action = random.randint(0, num_actions-1)

        # Q learning needs an argmax plus a write to each cell
        max_action = max((dict_q["%s,%s" % (state, x)] for x in range(num_actions) ) )

        dict_q["%s,%s" % (state, action)] = max_action + rnd.random()

def python_list_test():

    list_q = [0,] * (num_states * num_actions)

    for i in range(num_states * num_actions):
        state = random.randint(0, num_states-1)
        action = random.randint(0, num_actions-1)
        sa = state * num_actions + action

        max_action = max( (list_q[state + x] for x in range(num_actions)))

        list_q[sa] = max_action + rnd.random()

def numpy_test():

    # the numpy version
    numpy_q = np.zeros((num_states, num_actions), dtype='f')

    for i in range(num_states * num_actions):
        state = rnd.randint(0, num_states)
        action = rnd.randint(0, num_actions)

        max_action = np.amax(numpy_q[state])

        numpy_q[state,action] = max_action + rnd.random()


if __name__ == '__main__':
    print("Timing...")

    num = 2

    print("Numpy rand: ", timeit.timeit('k = rnd.randint(0, 200000)', 'import numpy.random as rnd'))
    print("Python rand: ", timeit.timeit('k = random.randint(0, 200001)', 'import random'))

    print("Python dict time: ", timeit.timeit(python_dict_test, number=num))
    print("Python list time: ", timeit.timeit(python_list_test, number=num))
    print("Numpy time: ", timeit.timeit(numpy_test, number=num))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
