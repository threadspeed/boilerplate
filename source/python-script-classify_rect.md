---
title: python script classify rect (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'classify rect'

Functions in program: 
* `def main(min_depth=1, max_depth=10):`

Modules used in program: 
* `import numpy`
* `import random`
* `import math`

## python classify rect

Python example: classify rect

```python
# coding: utf-8

import math
import random
from time import time
import numpy
from sklearn.tree import DecisionTreeClassifier
from sklearn.datasets import fetch_mldata
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
from decision_tree import FeatureComparisonTree


def main(min_depth=1, max_depth=10):
    x_all = numpy.array([(random.random(), random.random()) for i in range(10000)])
    y_all = numpy.array([int(x[0] > x[1]) for x in x_all])
    x_train, x_test, y_train, y_test = train_test_split(x_all, y_all, test_size=0.1)

    my_model1 = FeatureComparisonTree(x_train, y_train, max_depth=0)
    my_model2 = FeatureComparisonTree(x_train, y_train, max_depth=0, groups=[(0, 1)])
    my_model1.split_node()
    my_model2.split_node()

    for d in range(min_depth, max_depth + 1):
        sk_model = DecisionTreeClassifier(max_depth=d)
        sk_model.fit(x_train, y_train)
        sk_prediction = sk_model.predict(x_test)
        sk_accuracy = accuracy_score(y_test, sk_prediction)

        my_model1.add_depth()
        my_model2.add_depth()
        my_prediction1 = my_model1.predict(x_test)
        my_prediction2 = my_model2.predict(x_test)
        my_accuracy1 = accuracy_score(y_test, my_prediction1)
        my_accuracy2 = accuracy_score(y_test, my_prediction2)

        print('{}\t{}\t{}\t{}'.format(d, sk_accuracy, my_accuracy1, my_accuracy2))

if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
