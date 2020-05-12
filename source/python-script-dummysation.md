---
title: python script dummysation (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dummysation'

Functions in program: 
* `def work_dummies(X, idcpu):`

## python dummysation

Python mysql example: dummysation

```python
def work_dummies(X, idcpu):
    import pandas as pd
    ratio=20
    for col in X.columns:
        value_counts = X[col].value_counts().to_dict()
        if len(value_counts) <= 2:
            first_mod = value_counts.keys()[0]
            X[col+'_first_mod'] = X[col].map(lambda x: 1 if x == first_mod else 0)
            del X[col]
            continue
        to_dummy = X[col].map(lambda x : 'other' if value_counts[x] < X.shape[0]/ratio else x)
        dummies = pd.get_dummies(to_dummy, prefix='split_'+col, dummy_na=True)
        X = pd.concat([X, dummies], axis=1)
        del X[col]
    X.to_csv('datasets/X_categ_part_%s.csv' % idcpu, encoding='latin1', sep='|', float_format='%d')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
