---
title: python script aggregations (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'aggregations'

Functions in program: 
* `def Otherisation(df, colonne, howmany=10):`
* `def getLabelsColonne(dfgb, colonne):`
* `def getDummiesColonne(dfgb, colonne):`
* `def extracteurNbUniqueColonne(dfgb, colonne):`
* `def extracteurNbLigne(dfgb):`

## python aggregations

Python example: aggregations

```python
# Snippets for grouped dataframes (by customer id)
# Extractors
def extracteurNbLigne(dfgb):
    return dfgb.apply(lambda s : len(s))
def extracteurNbUniqueColonne(dfgb, colonne):
    return dfgb.apply(lambda s : len(s[colonne].unique()))
def getDummiesColonne(dfgb, colonne):
    return dfgb.apply(lambda s : pd.get_dummies(s.head(1)[colonne], prefix='du_'+colonne)).fillna(0)
def getLabelsColonne(dfgb, colonne):
    return dfgb.apply(lambda s : pd.get_dummies(s[colonne], prefix='du_'+colonne).cumsum().tail(1)).fillna(0)

# Otherisation
def Otherisation(df, colonne, howmany=10):
    assert howmany>1, 'Il faut au moins deux labels, dont un pour "other"'
    vcd = df[colonne].value_counts()
    return df[colonne].map(lambda s : s if s in vcd.keys()[:howmany-1] else 'other')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
