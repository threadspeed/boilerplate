---
title: python script mnist mytree (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mnist mytree'

Functions in program: 
* `def main(min_depth=1, max_depth=30):`

Modules used in program: 
* `import numpy`
* `import random`
* `import math`

## python mnist mytree

Python mysql example: mnist mytree

```python
# coding: utf-8

import math
import random
import numpy
from time import time
from sklearn.tree import DecisionTreeClassifier
from sklearn.datasets import fetch_mldata
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score
from decision_tree import FeatureComparisonTree

mnist = fetch_mldata('MNIST', data_home='.')


def main(min_depth=1, max_depth=30):
    X = mnist.data.toarray()
    Y = mnist.target

    x_train, x_test, y_train, y_test = train_test_split(X, Y, test_size=0.1)

    # 中央の14x14の画素を横向きにグループ化
    groups = [range(uo * 28 + 7, uo * 28 + 21) for uo in range(7, 21)]
    # 中央の14x14の画素を縦向きにグループ化
    groups += [[j * 28 + i for j in range(7, 21)] for i in range(7, 21)]
    model = FeatureComparisonTree(x_train, y_train, max_depth=min_depth-1, groups=groups)
    model.split_node()
    for d in range(min_depth, max_depth + 1):
        t0 = time()
        model.add_depth()
        t1 = time()
        prediction = model.predict(x_test)
        t2 = time()
        accuracy = accuracy_score(y_test, prediction)

        print('{}\t{}\t{}\t{}'.format(d, t1 - t0, t2 - t1, accuracy))

if __name__ == '__main__':
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
