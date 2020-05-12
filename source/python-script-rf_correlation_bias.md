---
title: python script rf correlation bias (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rf correlation bias'

Functions in program: 
* `def plot_variable_importances(flname, variable_importances, title):`
* `def generate_data(n_samples, n_correlated, corr_prob):`

Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import sys`
* `import random`

## python rf correlation bias

Python mysql example: rf correlation bias

```python
import random
import sys

import numpy as np
import matplotlib.pyplot as plt
from sklearn.ensemble import RandomForestClassifier

N_SAMPLES = 10
N_TREES = 100
MAX_CATEGORIES = 32
N_SIMS = 100

def generate_data(n_samples, n_correlated, corr_prob):
    n_features = 5 + n_correlated
    features = np.zeros((n_samples, n_features))
    labels = np.zeros(n_samples)

    for r in xrange(n_samples):
        labels[r] = random.randint(0, 1)

        for i in xrange(5):
            features[r, i] = random.randint(0, 1)

        for i in xrange(5, n_features):
            if random.random() < corr_prob:
                features[r, i] = labels[r]
            else:
                features[r, i] = random.randint(0, 1)

    return features, labels

def plot_variable_importances(flname, variable_importances, title):
    plt.clf()
    plt.boxplot(x=variable_importances)
    plt.xlabel("Variable", fontsize=16)
    plt.ylabel("Gini Importance", fontsize=16)
    plt.title(title, fontsize=18)
    plt.ylim([0.0, 1.0])
    plt.savefig(flname, DPI=200)

if __name__ == "__main__":
    # burn in
    for i in xrange(100):
        random.random()

    for corr_prob in [1.0, 0.75]:
        for n_correlated in [1, 2, 5, 10, 25]:
            variable_importances = [[] for i in xrange(5 + n_correlated)]
            for i in xrange(N_SIMS):
                print("Round", i)
                X, y = generate_data(N_SAMPLES, n_correlated, corr_prob)
                rf = RandomForestClassifier(n_estimators = N_TREES)
                rf.fit(X, y)
                feature_importances = rf.feature_importances_
                
                for i in xrange(len(feature_importances)):
                    variable_importances[i].append(feature_importances[i])

            plot_variable_importances(sys.argv[1] + "_corr_" + str(corr_prob) + "_" + str(n_correlated) + ".png", variable_importances, str(n_correlated) + " Correlated Variables")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
