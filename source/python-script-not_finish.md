---
title: python script not finish (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'not finish'


Modules used in program: 
* `import random`
* `import numpy as np`
* `import requests`

## python not finish

Python mysql example: not finish

```python
# -*- coding: utf-8 -*-
from sklearn.grid_search import GridSearchCV
from sklearn.linear_model import LogisticRegression
import requests
import numpy as np
import random

sample_num = 1400
dimension = 100

#Add request
requests.get('http://google.com')

X = []
y = []

for i in range(0, sample_num):
	x = []
	for j in range(0, dimension):
		x.append(random.random())
	X.append(x)
	y.append(i%2)

print('start gscv')

tuned_parameters = [{'C': [10]}]
gscv = GridSearchCV(LogisticRegression(class_weight='auto'), tuned_parameters, cv=2, n_jobs=-1)
gscv.fit(X, y)

print('finished')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
