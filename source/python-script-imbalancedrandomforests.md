---
title: python script imbalancedrandomforests (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'imbalancedrandomforests'


Modules used in program: 
* `import numpy as np`

## python imbalancedrandomforests

Python example: imbalancedrandomforests

```python
from collections import Counter

import numpy as np

from sklearn.metrics import precision_score, recall_score, classification_report, roc_curve
from sklearn.ensemble import RandomForestClassifier
from sklearn.datasets import make_classification
from sklearn.cross_validation import train_test_split
from sklearn.preprocessing import balance_weights

from mysmote import smote

x, y = make_classification(n_samples = 20000, n_features = 20, n_informative = 8, n_classes = 2, weights = [.99, .01])

x_train, x_test, y_train, y_test = train_test_split(x, y, test_size = .3, random_state = 42)

clf = RandomForestClassifier(n_estimators = 100)

## --- normal
clf_fit = clf.fit(x_train, y_train)

y_score = clf_fit.predict(x_test)

print(classification_report(y_test, y_score))
#               precision    recall  f1-score   support

#           0       0.99      1.00      0.99      5914
#           1       1.00      0.13      0.23        86

# avg / total       0.99      0.99      0.98      6000

## --- balance weights
clf_fit = clf.fit(x_train, y_train, sample_weight = balance_weights(y_train))

y_score = clf_fit.predict(x_test)

print(classification_report(y_test, y_score))
#               precision    recall  f1-score   support

#           0       0.99      1.00      0.99      5914
#           1       1.00      0.09      0.17        86

# avg / total       0.99      0.99      0.98      6000

## try to run through a set of weights

for C in ((np.arange(10.0) + 1) / 10):
    sample_weight = y_train.astype(float)
    sample_weight[sample_weight == 0] = C
    clf_fit = clf.fit(x_train, y_train, sample_weight = sample_weight)
    y_score = clf_fit.predict(x_test)
    print('-'*60)
    print('C:', C)
    print(precision_score(y_test, y_score, average = None))
    print(recall_score(y_test, y_score, average = None))
    
# ------------------------------------------------------------
# C: 0.1
# [ 0.98698264  1.        ]
# [ 1.          0.09302326]
# ------------------------------------------------------------
# C: 0.2
# [ 0.98731219  1.        ]
# [ 1.          0.11627907]
# ------------------------------------------------------------
# C: 0.3
# [ 0.98764195  1.        ]
# [ 1.          0.13953488]
# ------------------------------------------------------------
# C: 0.4
# [ 0.98780691  1.        ]
# [ 1.          0.15116279]
# ------------------------------------------------------------
# C: 0.5
# [ 0.98764195  1.        ]
# [ 1.          0.13953488]
# ------------------------------------------------------------
# C: 0.6
# [ 0.98698264  1.        ]
# [ 1.          0.09302326]
# ------------------------------------------------------------
# C: 0.7
# [ 0.98813701  1.        ]
# [ 1.         0.1744186]
# ------------------------------------------------------------
# C: 0.8
# [ 0.98780691  1.        ]
# [ 1.          0.15116279]
# ------------------------------------------------------------
# C: 0.9
# [ 0.98780691  1.        ]
# [ 1.          0.15116279]
# ------------------------------------------------------------
# C: 1.0
# [ 0.98764195  1.        ]
# [ 1.          0.13953488]

    
## --- SMOTE (Synthetic Minority Oversampling Technique)
s_train = smote(x_train[y_train == 1, :], 500, 5)

s_x_train = np.vstack((x_train, s_train))
s_y_train = np.hstack((y_train, np.repeat(1, s_train.shape[0])))
Counter(s_y_train)
# Counter({0: 13787, 1: 1278})

clf_fit = clf.fit(s_x_train, s_y_train)

y_score = clf_fit.predict(x_test)

print(classification_report(y_test, y_score))
#              precision    recall  f1-score   support

#           0       0.99      1.00      1.00      5914
#           1       0.97      0.36      0.53        86

# avg / total       0.99      0.99      0.99      6000

# when oversample is 2000
print(classification_report(y_test, y_score))
#               precision    recall  f1-score   support

#           0       0.99      1.00      1.00      5914
#           1       0.94      0.38      0.55        86

# avg / total       0.99      0.99      0.99      6000

## when oversample is 5000
print(classification_report(y_test, y_score))
#               precision    recall  f1-score   support

#           0       0.99      1.00      0.99      5914
#           1       0.80      0.37      0.51        86

# avg / total       0.99      0.99      0.99      6000

## --- get the most optimal portion of the ROC curve
y_scores = clf_fit.predict_proba(x_test)

fpr, tpr, threshold = roc_curve(y_test, y_scores[:,1])

## plot ROC curve
from matplotlib import pyplot as plt

plt.plot(fpr, tpr)
for i, j, k in zip(fpr[::2], tpr[::2], threshold[::2]):
    plt.text(i, j, str(round(k, 2)))
plt.xlabel('False Positive Rate')
plt.ylabel('True Positive Rate')
plt.show()

## get optimal false positive rate and true positive rate
## how much willing are you to get lose false positives for true positives
derivatives = (np.diff(tpr) + .001) / (np.diff(fpr) + .001)

plt.plot(threshold[:-1], derivatives)
plt.xlabel('Threshold')
plt.ylabel('Increase in Recall for each unit of Increase in False Positive Rate')
plt.show()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
