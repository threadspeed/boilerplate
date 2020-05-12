---
title: python script xgboost test (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'xgboost test'

Functions in program: 
* `def main():`
* `def make_dataset(n=500, d=10, c=2, z=2):`

Modules used in program: 
* `import xgboost as xgb`
* `import numpy as np`
* `import random`
* `import time`

## python xgboost test

Python mysql example: xgboost test

```python
# xgboost_test.py
# Author: Jacob Schreiber
#         jacob.schreiber@inria.fr

"""
Benchmarking scripts for XGBoost versus sklearn in terms of both time and
accuracy. 
"""

import time
import random
import numpy as np
import xgboost as xgb
from sklearn.ensemble import *

random.seed(0)
np.random.seed(0)

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
    The main comparison. Run sklearn, and then run xgboost using single and
    multi-threading options. 
    """

    # Generate the dataset
    X_train, X_test, y_train, y_test = make_dataset(10, z=100)
    n_estimators=1
    max_depth=1

    # sklearn goes first
    tic = time.time()
    clf = GradientBoostingClassifier(n_estimators=n_estimators, 
        max_depth=max_depth)
    clf.fit(X_train, y_train)
    print("sklearn: ",)
    print("Time: {}s".format(time.time() - tic), )
    print("Acc: {}".format(clf.score(X_test, y_test)),)
    print(y_test.sum())
    print(clf.predict(X_test))

    '''
    # Convert the data to DMatrix for xgboost
    dtrain = xgb.DMatrix(X_train, label=y_train)
    dtest  = xgb.DMatrix(X_test, label=y_test)

    # Loop through multiple thread numbers for xgboost
    for threads in 1, 2, 4, 16:
        # xgboost's sklearn interface
        tic = time.time()
        clf = xgb.XGBModel(n_estimators=n_estimators, max_depth=max_depth, 
            nthread=threads)
        clf.fit(X_train, y_train)
        print("xgboost-sklearn: ",)
        print("Time: {}s".format(time.time() - tic),)
        preds = np.round( clf.predict(X_test) )
        acc = 1. - (np.abs(preds - y_test).sum()  / y_test.shape[0])
        print("Acc: {}".format( acc ))


        print("xgboost {} threads: ".format( threads ))

        tic = time.time()
        param = { 
                  'max_depth' : max_depth, 
                        'eta' : 0.1, 
                      'silent': 1, 
                   'objective':'binary:logistic', 
                     'nthread': threads 
                }

        bst = xgb.train( param, dtrain, n_estimators, 
            [(dtest, 'eval'), (dtrain, 'train')] )
        
        print("Time: {}s".format(time.time() - tic),)
        preds = np.round(bst.predict(dtest) )
        acc = 1. - (np.abs(preds - y_test).sum() / y_test.shape[0])
        print("Acc: {}".format(acc))
    '''

if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
