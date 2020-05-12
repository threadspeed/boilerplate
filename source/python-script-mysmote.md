---
title: python script mysmote (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mysmote'

Functions in program: 
* `def smote(T, N, K):`

Modules used in program: 
* `import numpy as np`
* `import random`
* `import warnings`

## python mysmote

Python example: mysmote

```python
"""
SMOTE: Synthetic Minority Over-sampling Technique
Chawla, Bowyer, Hall, Kegelmeyer
Journal of Artificial Intelligence Research 16 (2002) 321-357

https://www.jair.org/media/953/live-953-2037-jair.pdf
"""

import warnings
import random

import numpy as np
from sklearn.neighbors import NearestNeighbors

def smote(T, N, K):
    """
    T ~ an array-like object representing the minority matrix
    N ~ the percent oversampling you want. e.g. 500 will give you 5 samples
    from the SMOTE algorithm (thus, has to be multiple of 100).
    K ~ K Nearest Neighbors
    """

    ## make sure T is an array with the proper dimensions
    T = np.asarray(T, dtype = np.float)
    nsamples = T.shape[0]
    nfeatures = T.shape[1]
    if nsamples < nfeatures:
        warnings.warn("Make sure the features are in the columns.")
    
    ## we want to oversample
    if N < 100:
        raise Exception("N should be at least 100")

    N = int(N) / 100

    nn = NearestNeighbors(K)
    
    nn.fit(T)

    synthetic = np.zeros([N * nsamples, nfeatures])
    
    for sample in xrange(nsamples):
        nn_minority = nn.kneighbors(T[sample], return_distance = False)[0]
        N_next = N
        
        newindex = 0
        while N_next != 0:
            k_chosen = random.randint(0, K - 1)
            while nn_minority[k_chosen] == sample: # don't pick itself
                k_chosen = random.randint(0, K - 1)                
            
            for feature in xrange(nfeatures):
                diff = T[nn_minority[k_chosen], feature] - T[sample, feature]
                gap = random.uniform(0, 1)
                synthetic[N*sample + newindex, feature] = T[sample, feature] + gap * diff

            newindex += 1
            N_next -= 1

    return synthetic

                
    



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
