---
title: python script groupby parallel (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'groupby parallel'

Functions in program: 
* `def applyParallel(dfGrouped, func):`

Modules used in program: 
* `import multiprocessing`
* `import pandas as pd`

## python groupby parallel

Python example: groupby parallel

```python
#Simple example with joblib

import pandas as pd
from joblib import Parallel, delayed
import multiprocessing

def applyParallel(dfGrouped, func):
    retLst = Parallel(n_jobs=multiprocessing.cpu_count())(delayed(func)(group) for name, group in dfGrouped)
    return pd.concat(retLst)
    
df_new = applyParallel(dfgb, func)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
