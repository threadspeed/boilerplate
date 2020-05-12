---
title: python script ens adv imports (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ens adv imports'


## python ens adv imports

Python example: ens adv imports

```python
#Bagging and Boosting models for both classification and regression problems
from sklearn.ensemble import RandomForestRegressor, ExtraTreesRegressor, BaggingRegressor
from sklearn.ensemble import RandomForestClassifier, ExtraTreesClassifier, BaggingClassifier
from sklearn.ensemble import GradientBoostingRegressor, AdaBoostRegressor
#import xgboost as xgb


#bagging algorithms for regression
rand_forest_reg = RandomForestRegressor(n_estimators=100, random_state=rand_seed)
extra_tree_reg = ExtraTreesRegressor(n_estimators=100,random_state=rand_seed)
#We use support vector regressor as our base model for bagging
bagging_meta_reg = BaggingRegressor(svr_reg, n_estimators=100, random_state=rand_seed)

#bagging algorithms for classification
rand_forest_cf = RandomForestClassifier(n_estimators=100, random_state=rand_seed)
extra_tree_cf = ExtraTreesClassifier(n_estimators=100, random_state=rand_seed)
#We use svc as our base model for bagging
bagging_meta_cf = BaggingClassifier(svc_cf, n_estimators=10, random_state=rand_seed)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
