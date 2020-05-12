---
title: python script rf (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rf'


## python rf

Python example: rf

```python
from sklearn.preprocessing import OrdinalEncoder
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestClassifier

from sksurv.preprocessing import OneHotEncoder
from sksurv.ensemble import RandomSurvivalForest

rstate = 124

# Split the data into train/test subsets
X_rf, y_rf = get_x_y_survival(data_cox, 'default_time', 'total_obs_time', 1)
X_rf_train, X_rf_test, y_rf_train, y_rf_test = train_test_split(X_rf, y_rf, test_size=0.25, random_state=rstate)

rsf = RandomSurvivalForest(n_estimators=50,
                           min_samples_split=7,
                           min_samples_leaf=10,
                           max_features="sqrt",
                           n_jobs=-1,
                           random_state=rstate,
                           verbose=1)

rsf.fit(X_rf_train, y_rf_train)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
