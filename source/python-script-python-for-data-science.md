---
title: python script python-for-data-science (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'python-for-data-science'


Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import matplotlib.mlab as mlab`
* `import random`
* `import numpy as np`
* `import pandas as pd`

## python python-for-data-science

Python mysql example: python-for-data-science

```python
# Import required libraries


import pandas as pd
import numpy as np
from sklearn.preprocessing import LabelEncoder
import random
from sklearn.ensemble import RandomForestClassifier
from sklearn.ensemble import GradientBoostingClassifier
from sklearn import metrics
from sklearn.metrics import roc_curve
from sklearn.metrics import auc
import matplotlib.mlab as mlab

import matplotlib.pyplot as plt


#y_scores=np.array([ 0.63, 0.53, 0.36, 0.02, 0.70 ,1 , 0.48, 0.46, 0.57])
#y_true=np.array([0, 1, 0, 0, 1, 1, 1, 1, 1])
#print(roc_curve(y_true, y_scores))

#read test and train data set

train = pd.read_csv('../train/train_data.csv')
test = pd.read_csv('../test/test_data.csv')
train['Type'] = 'Train' #Create a flag for Train and Test Data set
test['Type'] = 'Test'
fullData = pd.concat([train,test],axis=0) #Combined both Train and Test Data set

print(fullData.shape)

print(fullData.info())

fullData.boxplot(column='unit_sales', by='date')
print("BOXPLOT USING UNIT_SALES BY DATE")

fullData.boxplot(column='id', by='date')
print("BOXPLOT USING ID BY DATE")


#print(fullData)

#fullData['unit_sales'].value_counts().plot(kind="bar")
#plt.title('Unit Sales')
#plt.xlabel('Unit Sales')
#plt.ylabel('Count')

#sns.boxplot(data=fullData)

type_colors = ['#78C850',
                   '#F08030',
                   '#6890F0'
                   ]



#sns.countplot(x='date', data=fullData, palette=type_colors)


#View the column names / summary of the dataset

#print(fullData.columns) # This will show all the column names
#print(fullData.head(10)) # Show first 10 records of dataframe
#print(fullData.tail(10)) # Show last 10 records of dataframe
print(fullData.describe()) #You can look at summary of numerical fields by using describe() function

ID_col = ['id']
target_col = ['unit_sales']
data_col = ['store_nbr', 'onpromotion']
cat_cols = ['date', 'item_nbr']
other_col = ['Type'] #Test and Train Data set identifier
num_cols= list(set(list(fullData.columns))-set(cat_cols)-set(ID_col)-set(target_col)-set(other_col))


print("Num Cols")
print(num_cols)

print("Data Cols")
print(data_col)

print("Cat Cols")
print(cat_cols)

print("Other Cols")
print(other_col)

print("Target Cols")
print(target_col)
#variables with missing values and create a flag for those

#print(fullData.isnull().any()) #Will return the feature with True or False,True means have missing value else False

num_cat_cols = num_cols+cat_cols # Combined numerical and Categorical variables

for var in num_cat_cols:
    if fullData[var].isnull().any()==True:
        fullData[var+'_NA']=fullData[var].isnull()*1
        
#Impute numerical missing values with mean
fullData[num_cols] = fullData[num_cols].fillna(fullData[num_cols].mean(),inplace=True)

#Impute categorical missing values with -9999
fullData[cat_cols] = fullData[cat_cols].fillna(value = -9999)

#print(fullData[cat_cols])

#Create a label encoders for categorical variables and split the data set to train & test, further split the train data set to Train and Validate
#create label encoders for categorical features
for var in cat_cols:
 number = LabelEncoder()
 fullData[var] = number.fit_transform(fullData[var].astype('str'))
 #print(fullData[var])

plt.plot(fullData['unit_sales'])
plt.ylabel('sales count')
plt.show()

plt.plot(fullData['onpromotion'])
plt.ylabel('values')
plt.show()

plt.plot(fullData['item_nbr'])
plt.ylabel('item range')
plt.show()

#print(fullData)

#Target variable is also a categorical so convert it
fullData["unit_sales"] = number.fit_transform(fullData["unit_sales"].astype('str'))

train=fullData[fullData['Type']=='Train']
test=fullData[fullData['Type']=='Test']

#print(train)

train['is_train'] = np.random.uniform(0, 1, len(train)) <= .75
Train, Validate = train[train['is_train'] == True], train[train['is_train'] == False]

#Pass the imputed and dummy (missing values flags) variables into the modelling process. I am using random forest to predict the class
features=list(set(list(fullData.columns))-set(ID_col)-set(target_col)-set(other_col))

x_train = Train[list(features)].values
y_train = Train["unit_sales"].values
x_validate = Validate[list(features)].values
y_validate = Validate["unit_sales"].values
x_test=test[list(features)].values

random.seed(100)
rf = RandomForestClassifier(n_estimators=1000)
rf.fit(x_train, y_train)

#Check performance and make predictions

status = rf.predict_proba(x_validate) #float64 dtype

print(status[:,2].dtype)

#fpr, tpr, _ = roc_curve(y_validate, status[:,2], pos_label = 'None', sample_weight = 'None', drop_intermediate = 'True') #y_validate int64
#roc_auc = auc(fpr, tpr)
#print(roc_auc)

final_status = rf.predict_proba(x_test)
test["unit_sales"]=final_status[:,1]
print(test['unit_sales'].describe())

plt.plot(test['unit_sales'])
plt.ylabel('sales count (prediction)')
plt.show()

test.to_csv('../model_output.csv',columns=['id','unit_sales'])



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
