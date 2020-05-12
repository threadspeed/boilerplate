---
title: python script StandardScaler (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'StandardScaler'


Modules used in program: 
* `import pandas as pd`

## python StandardScaler

Python example: StandardScaler

```python
# tpot/operators/StandardScaler.py

from base import BasicOperator
from sklearn.preprocessing import StandardScaler
import pandas as pd

class StandardScaler(BasicOperator):
    def __init__(self):
        super(StandardScaler, self).__init__(
            func = KNeighborsClassifier, 
            intypes = [pd.DataFrame], 
            outtype = pd.DataFrame, 
            import_code = 'from sklearn.preprocessing import StandardScaler', 
            callable_code = 'knnc{} = KNeighborsClassifier(n_neighbors={})'
            )
    def callable_code(self, operator_num, operator, result_name):
        return '''
# Use Scikit-learn's StandardScaler to scale the features
training_features = {0}.loc[training_indices].drop('class', axis=1)
{1} = {0}.copy()
if len(training_features.columns.values) > 0:
    scaler = StandardScaler()
    scaler.fit(training_features.values.astype(np.float64))
    scaled_features = scaler.transform({1}.drop('class', axis=1).values.astype(np.float64))
    for col_num, column in enumerate({1}.drop('class', axis=1).columns.values):
        {1}.loc[:, column] = scaled_features[:, col_num]
'''.format(operator[2], result_name)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
