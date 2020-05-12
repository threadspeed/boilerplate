---
title: python script gbfc stability (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'gbfc stability'

Functions in program: 
* `def main():`
* `def make_dataset(n=500, d=10, c=2, z=2):`

Modules used in program: 
* `import numpy as np`
* `import random`
* `import time`

## python gbfc stability

Python example: gbfc stability

```python
# gbfc_stability.py
# Author: Jacob Schreiber
#         jacob.schreiber@inria.fr

"""
Benchmarking scripts for Gradient Boosting Machines in sklearn.
"""

import time
import random
import numpy as np
from sklearn.ensemble import *
from sklearn.tree import *

#random.seed(1)
#np.random.seed(1)

def make_dataset(n=500, d=10, c=2, z=2):
    """
    Make a dataset of size n, with d dimensions and m classes,
    with a distance of z in each dimension, making each feature equally
    informative.
    """

    # Generate our data and our labels
    X = np.concatenate([np.random.randn(n, d) + z*i for i in xrange(c)])
    y = np.concatenate([np.ones(n) * i for i in xrange(c)])

    # Generate a random indexing
    idx = np.arange(n*c)
    np.random.shuffle(idx)

    # Randomize the dataset, preserving data-label pairing
    X = X[idx]
    y = y[idx] 

    # Return x_train, x_test, y_train, y_test
    return X[::2], X[1::2], y[::2], y[1::2]

def main():
    """
    Look at the accuracy and speed of the GradientBoostingClassifier
    implementation on variable datasets.
    """

    # Generate the dataset
    X_train, X_test, y_train, y_test = make_dataset(5, z=100)

    # Properties of the estimator
    n_estimators=1
    max_depth=1

    # Run the time test
    tic = time.time()
    clf = GradientBoostingClassifier(n_estimators=n_estimators, 
        max_depth=max_depth)
    clf.fit(X_train, y_train)
    duration = time.time() - tic

    # Output the results
    print("{} positive test examples, {} negative test examples".format(
        y_test.sum(), y_test.shape[0] - y_test.sum() ) )
    print("GBM: Time: {}s, Accuracy: {}".format( duration, clf.score(X_test,y_test) ))
    print(clf.predict(X_test))

    # Run the time test
    tic = time.time()
    clf = DecisionTreeClassifier( max_depth=max_depth )
    clf.fit(X_train, y_train)
    duration = time.time() - tic
    print("Decision Tree: Time: {}s, Accuracy: {}".format( duration, clf.score(X_test,y_test) ))
    print(clf.predict(X_test))

if __name__ == '__main__':
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
