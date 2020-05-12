---
title: python script wineRegressionModel (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'wineRegressionModel'


Modules used in program: 
* `import pandas as pd`
* `import matplotlib.pyplot as plt`
* `import numpy as np`

## python wineRegressionModel

Python mysql example: wineRegressionModel

```python
#Data Preprocessing
    #import libraries
import numpy as np
import matplotlib.pyplot as plt
import pandas as pd
dataset = pd.read_csv('winemag-data-130k-v2.csv')
#print(dataset)
X = dataset.iloc[:,:-9].values #first colon means all rows, second means all columns but subtract last nine
np.set_printoptions(threshold = np.nan) #allows me to see the full array in python
#print(X)
X =  dataset.iloc[:,[1,5,9,6]].values
#print(y)
y = dataset.iloc[:,4].values
#print(X)
#taking care of missing data
from sklearn.preprocessing import Imputer
imputer = Imputer(missing_values = 'NaN', strategy = 'median', axis = 0) #making object of the class, technically mean is default but just doing it for fun, axis = 0 is mean of columns
#median seems to slightly increase accuracy of the machine
#X = X.reshape(-1, 1) this was for when X only had one columns
#X[1] = X[1].reshape(-1,1)

imputer = imputer.fit(X[:,1:2])
X[:,1:2] = imputer.transform(X[:,1:2])

#print("the below data is transformed: ")
#print(X[:,1:2])
y = y.reshape(-1,1)
imputer = imputer.fit(y)
y = imputer.transform(y)
#encoding categorical data
from sklearn.preprocessing import LabelEncoder, OneHotEncoder
labelencoder_X = LabelEncoder()
#this is for X[1]
X[:,0] = labelencoder_X.fit_transform(X[:,0].astype(str))
#X[:,1] is numbers its the price
X[:,2] = labelencoder_X.fit_transform(X[:,2].astype(str))
X[:,3] = labelencoder_X.fit_transform(X[:,3].astype(str))

OneHotEncoder = OneHotEncoder(categorical_features = [0,2,3])


#splitting data into training and test set
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(X,y, test_size = .25)

from sklearn.tree import DecisionTreeRegressor
#plt.plot(y,X, 'rx') #switched x and y so same inputs dont have different outputs
#plt.show()
regressor = DecisionTreeRegressor()
regressor = regressor.fit(X_train,y_train)
pred = regressor.predict(X_test)
print("the accuracy for Decision Tree regression model is: ")
print(regressor.score(X_test,y_test))#using regression got me an accuracy of about 35%
                                    #increases to about 37% after adding categorical data for country
                                    #increases to abt 41% with taster name
from sklearn.ensemble import RandomForestRegressor
regr = RandomForestRegressor() #accuracy abt 42% almost at 43% when i added the province column
regr = regr.fit(X_train, y_train.ravel())
print("the accuracy for Random Forest regression model is: ")
print(regr.score(X_test,y_test))

#this problem isn't really a classification problem
'''from sklearn.ensemble import RandomForestClassifier
clF = RandomForestClassifier()
clF = clF.fit(X_train, y_train.ravel())
pred = clF.predict(X_test)
from sklearn.metrics import accuracy_score
print("the accuracy for Random Forest classification model is: ")
print(accuracy_score(y_test, pred))

from sklearn.tree import DecisionTreeClassifier
clf = DecisionTreeClassifier()
clf  = clf.fit(X_train,y_train)
pred = clf.predict(X_test)

print("the accuracy for Decision Tree classification model is: ")
print(accuracy_score(y_test, pred))#using classification got me accuracy about 17%
                                   #increased to about 18% for country
                                   #increased to about 19%
                                   '''


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
