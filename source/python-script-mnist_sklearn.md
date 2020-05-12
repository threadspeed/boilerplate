---
title: python script mnist sklearn (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mnist sklearn'

Functions in program: 
* `def main(min_depth=1, max_depth=30):`

Modules used in program: 
* `import random`
* `import math`

## python mnist sklearn

Python mysql example: mnist sklearn

```python
# coding: utf-8

import math
import random
from time import time
from sklearn.tree import DecisionTreeClassifier
from sklearn.datasets import fetch_mldata
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score

mnist = fetch_mldata('MNIST', data_home='.')


def main(min_depth=1, max_depth=30):
    X = mnist.data
    Y = mnist.target

    x_train, x_test, y_train, y_test = train_test_split(X, Y, test_size=0.1)

    for d in range(min_depth, max_depth + 1):
        model = DecisionTreeClassifier(max_depth=d)
        t0 = time()
        model.fit(x_train, y_train)
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
