---
title: python script SimpleMixtureModel (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'SimpleMixtureModel'

Functions in program: 
* `def log_likelihood_two_1d_gauss(p, sample):`
* `def pdf_model(x, p):`

## python SimpleMixtureModel

Python example: SimpleMixtureModel

```python
# -*- coding: utf-8 -*-
# <nbformat>3.0</nbformat>

# <codecell>

from numpy import random
from scipy.optimize import minimize, show_options
from numpy.random import normal
from numpy import concatenate,array,zeros
from math import log,sqrt
# <codecell>
from scipy.stats import  norm
N = 1000
a = 0.3
s1 =  normal(0, 0.08, size=N*a)
s2 = normal(0.6,0.12, size=N*(1-a))
s = concatenate([s1,s2])
def pdf_model(x, p):
    mu1, sig1, mu2, sig2, pi_1 = p
    return pi_1*norm.pdf(x, mu1, sig1) + (1-pi_1)*norm.pdf(x, mu2, sig2)


def log_likelihood_two_1d_gauss(p, sample):
    return -log(pdf_model(sample, p)).sum()
max_iter=100
# Initial guess of parameters and initializations
p0 = array([-0.2,0.2,0.8,0.2,0.5])
mu1, sig1, mu2, sig2, pi_1 = p0
mu = array([mu1, mu2])
sig = array([sig1, sig2])
pi_ = array([pi_1, 1-pi_1])

gamma = zeros((2, s.size))
N_ = zeros(2)
p_new = p0
# EM loop
counter = 0
converged = False
while not converged:
    # Compute the responsibility func. and new parameters
    for k in [0,1]:
        gamma[k,:] = pi_[k]*norm.pdf(s, mu[k], sig[k])/pdf_model(s, p_new)
        N_[k] = 1.*gamma[k].sum()
        mu[k] = sum(gamma[k]*s)/N_[k]
        sig[k] = sqrt( sum(gamma[k]*(s-mu[k])**2)/N_[k] )
        pi_[k] = N_[k]/s.size
    p_new = [mu[0], sig[0], mu[1], sig[1], pi_[0]]
    assert abs(N_.sum() - N)/float(N) < 1e-6 
    assert abs(pi_.sum() - 1) < 1e-6
    # Convergence check
    counter += 1
    converged = counter >= max_iter


print("Means:   %6.3f  %6.3f" % (p_new[0], p_new[2]))
print("Std dev: %6.3f  %6.3f" % (p_new[1], p_new[3]))
print("Mix (1): %6.3f " % p_new[4])





```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
