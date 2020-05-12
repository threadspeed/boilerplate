---
title: python script resampling (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'resampling'


## python resampling

Python example: resampling

```python
from sklearn.linear_model import LogisticRegression
from imblearn.over_sampling import RandomOverSampler
from imblearn.under_sampling import RandomUnderSampler

# Sur-échantillonnage
rOs = RandomOverSampler()
X_ro, y_ro = rOs.fit_resample(X_train, y_train)
# Entraînement du modèle de régression logistique
lr = LogisticRegression()
lr.fit(X_ro, y_ro)
# Affichage des résultats
y_pred = lr.predict(X_test)
print(classification_report_imbalanced(y_test, y_pred))

# Sous-échantillonnage
rUs = RandomUnderSampler()
X_ru, y_ru = rUs.fit_resample(X_train, y_train)
# Entraînement du modèle de régression logistique
lr.fit(X_ru, y_ru)
# Affichage des résultats
y_pred = lr.predict(X_test)
print(classification_report_imbalanced(y_test, y_pred))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
