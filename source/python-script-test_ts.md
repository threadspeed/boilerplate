---
title: python script test ts (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test ts'


Modules used in program: 
* `import random`

## python test ts

Python mysql example: test ts

```python
execfile("core.py")
from ts import *
import random

random.seed(1)
means = [0.1, 0.1, 0.1, 0.1, 0.9]
n_arms = len(means)
random.shuffle(means)
arms = map(lambda (mu): BernoulliArm(mu), means)
print("Best arm is " + str(ind_max(means)))

algo = ThompsonSampling([], [], [])
algo.initialize(n_arms)
results = test_algorithm(algo, arms, 5000, 250)

f = open("ts_results.tsv", "w")

for i in range(len(results[0])):
    f.write("\t".join([str(results[j][i]) for j in range(len(results))]) + "\n")

f.close()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
