---
title: python script runner (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'runner'


Modules used in program: 
* `import copy`
* `import random`

## python runner

Python mysql example: runner

```python
# coding: utf-8
import random
import copy

TARGET_ELEMENT_SIZE = 10

class Runner:
    def __init__(self, input=None):
       self.env = SortEnvironment(range(TARGET_ELEMENT_SIZE), input)
       self.step_num = 0

    def step(self, action, verbose=False):
        action.do(self.env)
        if verbose:
            print('step %d, %s' % (self.step_num, action))
            print('%s -> %s' % (self.env.old_state, self.env.current))
        self.step_num += 1

    def finished(self):
        return self.env.collected()


class SortEnvironment:
    def __init__(self, collect_answer, input=None):
        if not input:
            self.current = random.sample(collect_answer, len(collect_answer))
        else:
            self.current = input
        self.collect_answer = collect_answer
        self.old_state = copy.copy(self.current)

    @property
    def current_exp(self):
        return ','.join([str(s) for s in self.current])

    @property
    def old_state(self):
        return self.old_state

    @property
    def collect_answer(self):
        return self.collect_answer

    def collected(self):
        return self.current == self.collect_answer

    def biggerThan(self, pos_a, pos_b):
        return self.current[pos_a] > self.current[pos_b]

    def swap(self, pos_a, pos_b):
        self.old_state = copy.copy(self.current)
        a = self.current[pos_a]
        b = self.current[pos_b]
        self.current[pos_a] = b
        self.current[pos_b] = a


class SwapPosAAndPosB:
    def __init__(self, pos_a, pos_b):
        self.pos_a = pos_a
        self.pos_b = pos_b

    def do(self, env):
        env.swap(self.pos_a, self.pos_b)

    def __repr__(self):
        return 'SwapPosAAndPosB(%d,%d)' % (self.pos_a, self.pos_b)


actions = []
for i in range(TARGET_ELEMENT_SIZE):
    actions += [ SwapPosAAndPosB(i,j) for j in range(TARGET_ELEMENT_SIZE) if i != j and i > j ]

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
