---
title: python script Income+RandomTree (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Income+RandomTree'

Functions in program: 
* `def warn(*args, **kwargs):`
* `def warn(*args, **kwargs):`

Modules used in program: 
* `import pandas as pd`
* `import warnings`
* `import pandas as pd`
* `import warnings`

## python Income+RandomTree

Python mysql example: Income+RandomTree

```python
def warn(*args, **kwargs):
    pass
import warnings
warnings.warn = warn

import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn import tree
from sklearn.ensemble import RandomForestClassifier

income_data = pd.read_csv("income.csv", header = 0, delimiter = ", ")
#print(income_data.iloc[0])

labels = income_data[["income"]]
#The gender disparity is REAL, let's turn sex into a binary val
#New col "sex-bin" where Male = 0 , Female = 1
income_data["sex-bin"] = income_data["sex"].apply(lambda row: 0 if row == "Male" else 1)

#Let's add the country of origin too! There seems to be a lot of people in th e US so... Let's make USA = 0
income_data["country-bin"] = income_data["native-country"].apply(lambda row: 0 if row == "United-States" else 1)


def warn(*args, **kwargs):
    pass
import warnings
warnings.warn = warn

import pandas as pd
from sklearn.model_selection import train_test_split
from sklearn import tree
from sklearn.ensemble import RandomForestClassifier

income_data = pd.read_csv("income.csv", header = 0, delimiter = ", ")
#print(income_data.iloc[0])

labels = income_data[["income"]]
#The gender disparity is REAL, let's turn sex into a binary val
#New col "sex-bin" where Male = 0 , Female = 1
income_data["sex-bin"] = income_data["sex"].apply(lambda row: 0 if row == "Male" else 1)

#Let's add the country of origin too! There seems to be a lot of people in th e US so... Let's make USA = 0
income_data["country-bin"] = income_data["native-country"].apply(lambda row: 0 if row == "United-States" else 1)


##########################

data = income_data[["age","capital-gain","capital-loss","hours-per-week","sex-bin","country-bin"]]


train_data,test_data,train_labels,test_labels = train_test_split(data,labels,random_state = 1)

forest = RandomForestClassifier(random_state = 1)

forest.fit(train_data,train_labels)
print(forest.feature_importances_)
print("Forest accuracy is:"+ str(forest.score(test_data,test_labels)))

########################
tree = tree.DecisionTreeClassifier(random_state = 1)

tree.fit(train_data,train_labels)
print("Tree accuracy is:" +str(tree.score(test_data,test_labels)))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
