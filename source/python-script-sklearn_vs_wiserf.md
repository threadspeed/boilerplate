---
title: python script sklearn vs wiserf (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sklearn vs wiserf'


Modules used in program: 
* `import random`
* `import numpy`

## python sklearn vs wiserf

Python example: sklearn vs wiserf

```python
import numpy
import random
from sklearn.datasets import fetch_mldata
mnist = fetch_mldata('MNIST original')
# Define training and testing sets
inds = numpy.arange(len(mnist.data))
test_i = random.sample(xrange(len(inds)), int(0.1*len(inds)))
train_i = numpy.delete(inds, test_i)
X_train = mnist.data[train_i].astype(numpy.double)
y_train = mnist.target[train_i].astype(numpy.double)
X_test = mnist.data[test_i].astype(numpy.double)
y_test = mnist.target[test_i].astype(numpy.double)

# scikit-learn single core, MNIST data
from time import time
from sklearn.ensemble import RandomForestClassifier
t1 = time()
rf = RandomForestClassifier(n_estimators=10, max_features="sqrt", n_jobs=1)
rf.fit(X_train, y_train)
score = rf.score(X_test, y_test)
t2 = time()
dt = t2-t1
print("RandomForestClassifier: Accuracy: %0.2f\t%0.2fs" % (score, dt))

from sklearn.ensemble import ExtraTreesClassifier
t1 = time()
rf = ExtraTreesClassifier(n_estimators=10, max_features="sqrt", n_jobs=1)
rf.fit(X_train, y_train)
score = rf.score(X_test, y_test)
t2 = time()
dt = t2-t1
print("ExtraTreesClassifier: Accuracy: %0.2f\t%0.2fs" % (score, dt))

# wiseRF single core, MNIST data
from PyWiseRF import WiseRFClassifier
t1 = time()
rf = WiseRFClassifier(n_estimators=10, n_jobs=1) # max_features=auto == sqrt
rf.fit(X_train, y_train)
score = rf.score(X_test, y_test)
t2 = time()
dt = t2-t1
print("WiseRFClassifier Accuracy: %0.2f\t%0.2fs" % (score, dt))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
