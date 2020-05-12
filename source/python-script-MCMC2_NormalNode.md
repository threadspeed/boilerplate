---
title: python script MCMC2 NormalNode (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MCMC2 NormalNode'


Modules used in program: 
* `import numpy as np`
* `import matplotlib.pyplot as plt`
* `import random`
* `import math`

## python MCMC2 NormalNode

Python mysql example: MCMC2 NormalNode

```python
__author__ = 'guopei'

import math
import random
import matplotlib.pyplot as plt
import numpy as np
from scipy.stats import norm

class NormalNode:
    def __init__(self, init_value, name, mean, var, candsd = 0, observed = False):
        self.name = name
        self.candsd = float(candsd)
        self.value = init_value
        self.observed = observed

        self.children = []
        self.sample_values = []

        # if mean is a value, then mean() method return mean
        if type(mean) == float or type(mean) == int:
            self.mean = lambda : float(mean)
        # if mean is a node class, then mean() return mean.value
        else:
            self.mean = lambda :  mean.value
            mean.children.append(self)

        # same thing with mean
        if type(var) == float or type(var) == int:
            self.var = lambda :  float(var)
        else:
            self.var = lambda :  var.value
            var.children.append(self)


    def sample(self):

        last = self.value
        cand = random.gauss(last, self.candsd)


        cand_prob = self.get_log_posterior_prob(cand)
        current_prob = self.get_log_posterior_prob(last)

        rand = math.log(random.random())

        if rand < cand_prob - current_prob:
            self.value = cand

        self.sample_values.append(self.value)


    def get_log_posterior_prob(self, value):

        prob = self.get_log_likelihood_prob(value)

        for chld in self.children:
            prob += self.get_log_observed_prob(chld.value, value, chld.var())

        return prob


    # get probability of node value given its mean and var
    def get_log_likelihood_prob(self, x):

        # find current value of mean and var
        miu = self.mean()
        sig2 = self.var()

        return - (x - miu) ** 2 / (2 * sig2)

    # get probability of the observed data given node value(mean) and corresponding var
    def get_log_observed_prob(self, data, miu, sig2):

        return - (data - miu) ** 2 / (2 * sig2)

    def draw_mixing(self, burn_in = 0):
        fig = plt.figure()
        fig.suptitle('{} mixing'.format(self.name), fontsize=14, fontweight='bold')

        data = self.sample_values[burn_in:]
        plt.plot(data)

        plt.show()

    def draw_hist(self, mean, var, burn_in = 0):

        fig = plt.figure()
        fig.suptitle('{} prior and post distribution'.format(self.name), fontsize=14, fontweight='bold')

        data = self.sample_values[burn_in:]


        x = np.linspace(0, 10, num=1000)
        y = (1 / (2 * math.pi * var) ** 0.5) * np.exp(-1 / (2 * var) * (x - mean) ** 2)
        plt.plot(x,y)

        weights = y.max() * np.ones_like(data)/float(len(data))
        plt.hist(data, bins=50, normed=True, color="Green")

        plt.ylim(ymin=0)
        plt.xlim(5, 6.5)

        plt.show()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
