---
title: python script RandomForest (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'RandomForest'


## python RandomForest

Python mysql example: RandomForest

```python
# tpot/operators/RandomForest.py

from base import LearnerOperator
from sklearn.ensemble import RandomForestClassifier
from pandas as pd

class RandomForest(LearnerOperator):
    def __init__(self):
        super(RandomForest, self).__init__(
            func = RandomForestClassifier, 
            intypes = [pd.DataFrame, int, int], 
            outtype = pd.DataFrame, 
            import_code = 'from sklearn.ensemble import RandomForestClassifier', 
            callable_code = 'rfc{} = RandomForestClassifier(n_estimators={}, max_features={})'
            )        

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
