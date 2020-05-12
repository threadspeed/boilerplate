---
title: python script KNNc (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'KNNc'


Modules used in program: 
* `import pandas as pd`

## python KNNc

Python example: KNNc

```python
# tpot/operators/KNNc.py

from base import LearnerOperator
from sklearn.neighbors import KNeighborsClassifier
import pandas as pd

class KNNc(LearnerOperator):
    def __init__(self):
        super(KNNc, self).__init__(
            func = KNeighborsClassifier, 
            intypes = [pd.DataFrame, int], 
            outtype = pd.DataFrame, 
            import_code = 'from sklearn.neighbors import KNeighborsClassifier', 
            callable_code = 'knnc{} = KNeighborsClassifier(n_neighbors={})'
            )    
            

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
