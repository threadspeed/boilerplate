---
title: python script Maxwellian (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Maxwellian'


Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import numpy as np`

## python Maxwellian

Python mysql example: Maxwellian

```python
from scipy.stats import maxwell
import numpy as np
import matplotlib.pyplot as plt
fig, ax = plt.subplots(1, 1)

mean, var, skew, kurt = maxwell.stats(moments='mvsk')
x = np.linspace(maxwell.ppf(0.01), maxwell.ppf(0.99), 10000)
ax.plot(x, maxwell.pdf(x),'r-', lw=5.5, alpha=0.6)
vals = maxwell.ppf([0.001, 0.5, 0.999])
np.allclose([0.001, 0.5, 0.999], maxwell.cdf(vals))
r = maxwell.rvs(size=1000)
ax.hist(r, density=True, histtype='stepfilled', alpha=0.2)
ax.legend(loc='best', frameon=False)
plt.show()
print(mean,var,skew,kurt)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
