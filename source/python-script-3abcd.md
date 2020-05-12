---
title: python script 3abcd (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '3abcd'

Functions in program: 
* `def gauss_prob(min, max, σ, µ):`
* `def gauss_fn(σ, µ):`

Modules used in program: 
* `import math`
* `import numpy as np`
* `import matplotlib.pyplot as plt`

## python 3abcd

Python example: 3abcd

```python
#!/usr/bin/env python3
# -*- coding: utf-8 -*-
"""
Created on Tue Apr 30 20:46:26 2019

@author: Bormann, Lewin; Jürgens, Kira; Leung, Emily
"""

import matplotlib.pyplot as plt
import numpy as np

import math

data = np.loadtxt("DateiBlatt4.csv")
bins_per_int = 3


# 3a)
fig = plt.figure(dpi=150)
ax = fig.add_subplot(111)
ax.grid(True)

bins = np.linspace(data.min(), data.max(), int((data.max()-data.min())*bins_per_int))
ax.hist(data, bins=bins)

# Wir berechnen die Werte einmal händisch, dann mit numpy-Methoden.
# 3b)

mean = data.sum() / data.size
print("Average:", data.mean(), mean)
err = math.sqrt(1/(data.size-1) * 1/data.size * ((data - mean)**2).sum())
print("Statistical error:", math.sqrt(1/(data.size) * data.var(ddof=1)), err)

# 3c)

stddev = math.sqrt(1/(data.size-1) * ((data -  mean)**2).sum())
print("Standard deviation:", data.std(ddof=1), stddev)

# Wähle Parameter σ = stddev, µ = mean

def gauss_fn(σ, µ):
    def gauss(x):
        return 1/(math.sqrt(2*math.pi)*σ) * math.exp(-(x - µ)**2/(2*σ**2))
    return np.vectorize(gauss)

def gauss_prob(min, max, σ, µ):
    """Calculates the probability of events between min and max.

    min and max can be None to express +/- Inf."""
    upper = 1 if max is None else math.erf((max - µ)/(math.sqrt(2)*σ))
    lower = 0 if min is None else math.erf((min - µ)/(math.sqrt(2)*σ))
    return 1/2 * (upper - lower)

# Berechne Integral für jede Balkenbreite, um die Zahlen direkt zu vergleichen.
x = np.zeros(bins.size-1)
y = np.zeros(x.size)
for (i, min) in enumerate(bins[:-1]):
    mid = (bins[i]+bins[i+1])/2
    x[i] = mid
    delta = (bins[i+1]-bins[i])/2
    y[i] = gauss_prob(mid-delta, mid+delta, stddev, mean) * data.size

ax.plot(x, y, 'rx-')
ax.plot(x, gauss_fn(stddev, mean)(x) * data.size/3, 'go-')

# 3d)

print("P(X > 3.5) =", gauss_prob(3.5, None, stddev, mean))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
