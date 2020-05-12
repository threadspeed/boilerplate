---
title: python script rf bias (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rf bias'

Functions in program: 
* `def plot_variable_importances(flname, variable_importances, title):`
* `def generate_stacked(n_samples, max_categories):`
* `def generate_onehot(n_samples, max_categories):`

Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import sys`
* `import random`

## python rf bias

Python mysql example: rf bias

```python
import random
import sys

import numpy as np
import matplotlib.pyplot as plt
from sklearn.ensemble import RandomForestClassifier

N_SAMPLES = 1000
N_TREES = 100
MAX_CATEGORIES = 32
N_SIMS = 100

def generate_onehot(n_samples, max_categories):
    n_features = 0
    variable_indices = [0]
    for i in xrange(2, max_categories + 1):
        n_features += i
        variable_indices.append(n_features)
    
    features = np.zeros((n_samples, n_features))
    labels = np.zeros((n_samples))
    for r in xrange(n_samples):
        labels[r] = random.randint(0, 1)

        for c in xrange(n_features):
            features[r, c] = random.randint(0, 1)

    return features, labels, variable_indices

def generate_stacked(n_samples, max_categories):
    n_features = max_categories - 1

    features = np.zeros((n_samples, n_features))
    labels = np.zeros((n_samples))
    for r in xrange(n_samples):
        labels[r] = random.randint(0, 1)

        for c in xrange(n_features):
            n_categories = c + 2
            features[r, c] = random.randint(0, n_categories - 1)

    return features, labels

def plot_variable_importances(flname, variable_importances, title):
    plt.clf()
    plt.boxplot(x=variable_importances)
    plt.xlabel("Variable", fontsize=16)
    plt.ylabel("Gini Importance", fontsize=16)
    plt.title(title, fontsize=18)
    plt.savefig(flname, DPI=200)

if __name__ == "__main__":
    # burn in
    for i in xrange(100):
        random.random()

    variable_importances = [[] for i in xrange(MAX_CATEGORIES - 1)]
    for i in xrange(N_SIMS):
        print("Round", i)
        X, y, variable_indices = generate_onehot(N_SAMPLES, MAX_CATEGORIES)
        rf = RandomForestClassifier(n_estimators = N_TREES)
        rf.fit(X, y)
        feature_importances = rf.feature_importances_

        for i, (start, end) in enumerate(zip(variable_indices[:-1], variable_indices[1:])):
            variable_importances[i].extend(feature_importances[start:end])

    plot_variable_importances(sys.argv[1], variable_importances, "One-Hot Encoded")

    variable_importances = [[] for i in xrange(MAX_CATEGORIES - 1)]
    for i in xrange(N_SIMS):
        print("Round", i)
        X, y = generate_stacked(N_SAMPLES, MAX_CATEGORIES)
        rf = RandomForestClassifier(n_estimators = N_TREES)
        rf.fit(X, y)
        feature_importances = rf.feature_importances_

        for i in xrange(MAX_CATEGORIES - 1):
            variable_importances[i].append(feature_importances[i])

    plot_variable_importances(sys.argv[2], variable_importances, "Integer Encoded")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
