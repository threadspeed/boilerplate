---
title: python script MCMC2 InvGammaNode (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MCMC2 InvGammaNode'


Modules used in program: 
* `import numpy as np`
* `import matplotlib.pyplot as plt`
* `import random`
* `import math`

## python MCMC2 InvGammaNode

Python mysql example: MCMC2 InvGammaNode

```python
__author__ = 'guopei'

import math
import random
import matplotlib.pyplot as plt
import numpy as np

class InvGammaNode:
    def __init__(self, init_value, name, shape, scale, candsd = 0, observed = False):
        self.name = name
        self.candsd = float(candsd)
        self.value = init_value
        self.observed = observed

        self.children = []
        self.sample_values = []

        # if alpha is a value, then alpha() method return alpha
        if type(shape) == float or type(shape) == int:
            self.alpha = lambda :  float(scale)
        # if alpha is a node class, then alpha() return alpha.value
        else:
            self.alpha = lambda :  shape.value
            shape.children.append(self)

        # same thing with alpha
        if type(scale) == float or type(scale) == int:
            self.beta = lambda :  float(scale)
        else:
            self.beta = lambda :  scale.value
            scale.children.append(self)


    def sample(self):

        # InvGamma is defined on > 0 only
        last = self.value
        cand = random.gauss(last, self.candsd)
        if cand <= 0:
            self.sample_values.append(self.value)
            return

        cand_prob = self.get_log_posterior_prob(cand)
        current_prob = self.get_log_posterior_prob(last)

        rand = math.log(random.random())
        if rand < cand_prob - current_prob:
            self.value = cand

        self.sample_values.append(self.value)

    def get_log_posterior_prob(self, value):

        prob = self.get_log_likelihood_prob(value)

        for chld in self.children:
            prob += self.get_log_observed_prob(chld.value, chld.mean(), value)

        return prob

    # get probability of node value given its alpha and beta
    def get_log_likelihood_prob(self, x):

        # find current value of mean and var
        alpha = self.alpha()
        beta = self.beta()

        return - (alpha + 1) * math.log(x) - beta / x

    # get probability of the child node give all its parents node including self
    def get_log_observed_prob(self, data, miu, sig2):

        return - math.log(sig2) - (data - miu) ** 2 / (2 * sig2)

    def draw_mixing(self, burn_in = 0):
        fig = plt.figure()
        fig.suptitle('{} mixing'.format(self.name), fontsize=14, fontweight='bold')

        data = self.sample_values[burn_in:]
        plt.plot(data)

        plt.show()

    def draw_hist(self, alpha, beta, burn_in = 0):

        fig = plt.figure()
        fig.suptitle('{} prior and post distribution'.format(self.name), fontsize=14, fontweight='bold')

        data = self.sample_values[burn_in:]
        plt.hist(data, bins=50, normed=True, color="Green")

        x = np.linspace(0.001, 1, num=1000)
        y = (beta ** alpha / math.gamma(alpha) * np.power(x, (-alpha - 1)) * np.exp(-beta / x))
        plt.plot(x,y)

        plt.ylim(ymin=0)
        plt.xlim(xmin=0.001, xmax=1)

        plt.show()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
