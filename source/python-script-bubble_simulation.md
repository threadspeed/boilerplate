---
title: python script bubble simulation (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'bubble simulation'


## python bubble simulation

Python mysql example: bubble simulation

```python
from base_bubble_tools import bernoulli_sample


class Test:

    def __init__(self, bubble):
        self.bubble = bubble
        self.data = []
        
    def simulate_one(self, p=.01):
        if bernoulli_sample(p):
            self.data.append(1)
        else:
            self.data.append(0)


    def simulate_n(self, n, p=.01):
        for i in range(n):
            self.simulate_one(p)

    def is_success(self, threshold=0):
        return sum(self.data) > 0


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
