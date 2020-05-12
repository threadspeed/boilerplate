---
title: python script pickling an sklearn classifier w custom transformer attempt (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pickling an sklearn classifier w custom transformer attempt'

Functions in program: 
* `def generate_model():`

Modules used in program: 
* `import random as rnd`
* `import numpy as np`
* `import pandas as pd`
* `import yaml`
* `import sys`
* `import pickle`
* `import datetime`
* `import boto`

## python pickling an sklearn classifier w custom transformer attempt

Python example: pickling an sklearn classifier w custom transformer attempt

```python
import boto
import datetime
import pickle
import sys
import yaml
from os.path import dirname, join
from sklearn.externals import joblib

import pandas as pd
import numpy as np
import random as rnd

from scipy import sparse

from sklearn.base import BaseEstimator, TransformerMixin
from sklearn.ensemble import RandomForestClassifier
from sklearn.feature_extraction.text import CountVectorizer, TfidfVectorizer
from sklearn.naive_bayes import GaussianNB, MultinomialNB
from sklearn.linear_model import LogisticRegression, Perceptron
from sklearn.linear_model import SGDClassifier
from sklearn.metrics import classification_report
from sklearn.neural_network.multilayer_perceptron import MLPClassifier
from sklearn.model_selection import GridSearchCV, train_test_split, cross_val_score, cross_val_predict
from sklearn.pipeline import FeatureUnion, Pipeline
from sklearn.neighbors import KNeighborsClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.svm import SVC, LinearSVC



class ItemSelector(BaseEstimator, TransformerMixin):
    def __init__(self, key):
        self.key = key

    def fit(self, x, y=None):
        return self

    def transform(self, data_dict):
        return data_dict[self.key]


def generate_model():

    with open(join(dirname(dirname(__file__)), 'config_single_model.yml')) as f:
        config = yaml.safe_load(f)

    with open(join(dirname(dirname(__file__)), 'data/data.csv')) as f:
        data_df = pd.read_csv(f)

    pipeline = Pipeline([

        ('union', FeatureUnion(
            transformer_list=[

                ('title', Pipeline([
                    ('selector', ItemSelector(key='title')),
                    ('vec', TfidfVectorizer(ngram_range=[1, 1], max_features=500)),
                ])),

                ('url', Pipeline([
                    ('selector', ItemSelector(key='url')),
                    ('vec', TfidfVectorizer(ngram_range=[1, 1], max_features=500)),
                ])),

            ],

        )),

        ('estimator_cls', MultinomialNB(alpha=20.0)),
    ])

    X_train, X_test, Y_train, Y_test = train_test_split(
        data_df[['title', 'url']],
        data_df['noneng'],
        test_size=0.25, random_state=42
    )

    clf = pipeline.fit(X_train, Y_train)

    joblib.dump(clf, 'model.pkl')



if __name__ == '__main__':

    generate_model()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
