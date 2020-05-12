---
title: python script chronic kidney disease12 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'chronic kidney disease12'


## python chronic kidney disease12

Python example: chronic kidney disease12

```python
from sklearn.naive_bayes import GaussianNB

clf_NB = GaussianNB()
model_NB = clf_NB.fit(X_train,y_train)
predictions_NB = clf_NB.predict(X_test)
accuracy_NB =accuracy_score(y_test, predictions_NB)
fscore_NB=fbeta_score(y_test, predictions_NB,beta = 0.5)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
