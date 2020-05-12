---
title: python script recruit rfregress (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'recruit rfregress'

Functions in program: 
* `def evaluate(model, test_features, test_labels):`

## python recruit rfregress

Python mysql example: recruit rfregress

```python
from sklearn.feature_selection import RFE
from sklearn.linear_model import LogisticRegression
from sklearn import metrics
from sklearn.ensemble import RandomForestClassifier

model = LogisticRegression()
rfe = RFE(model,12)
rfe = rfe.fit(emp_train[x],emp_train[y])

print(rfe.support_)
print(rfe.ranking_)

cols = ['department', 'region', 'education', 'gender', 'recruitment_channel', 'no_of_trainings', 'age', 'previous_year_rating', 'length_of_service', 'KPIs_met >80%', 'awards_won?', 'avg_training_score', 'training_scr_35_50', 'training_scr_50_65', 'training_scr_65_80', 'training_scr_85_100', 'age_18_25', 'age_25_35', 'age_35_45', 'age_45_60', 'age_training', 'KPI_training', 'education_age', 'region_max', 'len_serv_0_5', 'len_serv_5_10', 'len_serv_10_15', 'len_serv_15_20', 'len_serv_25']
X = emp_train[cols]
y = emp_train['is_promoted']

from sklearn.cross_validation import train_test_split
X_train, y_train = X,y
X_test = emp_test[cols]


rf = RandomForestClassifier()
rf.fit(X_train, y_train)

y_pred = rf.predict(X_test)
X_test['is_promoted'] = y_pred
X_test['employee_id'] = employee_id

sub = X_test.loc[:,['employee_id','is_promoted']]
print(sub.shape)

from sklearn.ensemble import RandomForestRegressor
rf = RandomForestRegressor(random_state = 42)
from pprint(import pprint)

pprint(rf.get_params())
from sklearn.model_selection import RandomizedSearchCV

# Number of trees in random forest
n_estimators = [int(x) for x in np.linspace(start = 200, stop = 2000, num = 10)]
# Number of features to consider at every split
max_features = ['auto', 'sqrt']
# Maximum number of levels in tree
max_depth = [int(x) for x in np.linspace(10, 110, num = 11)]
max_depth.append(None)
# Minimum number of samples required to split a node
min_samples_split = [2, 5, 10]
# Minimum number of samples required at each leaf node
min_samples_leaf = [1, 2, 4]
# Method of selecting samples for training each tree
bootstrap = [True, False]

# Create the random grid
random_grid = {'n_estimators': n_estimators,
               'max_features': max_features,
               'max_depth': max_depth,
               'min_samples_split': min_samples_split,
               'min_samples_leaf': min_samples_leaf,
               'bootstrap': bootstrap}

pprint(random_grid)

rf = RandomForestRegressor(random_state = 42)
# Random search of parameters, using 3 fold cross validation, 
# search across 100 different combinations, and use all available cores
rf_random = RandomizedSearchCV(estimator=rf, param_distributions=random_grid,
                              n_iter = 100, scoring='neg_mean_absolute_error', 
                              cv = 3, verbose=2, random_state=42, n_jobs=-1,
                              return_train_score=True)

# Fit the random search model
rf_random.fit(X_train, y_train);
rf_random.best_params_
rf_random.cv_results_

def evaluate(model, test_features, test_labels):
    predictions = model.predict(test_features)
    errors = abs(predictions - test_labels)
    mape = 100 * np.mean(errors / test_labels)
    accuracy = 100 - mape
    print('Model Performance')
    print('Average Error: {:0.4f} degrees.'.format(np.mean(errors)))
    print('Accuracy = {:0.2f}%.'.format(accuracy))
    return accuracy

base_model = RandomForestRegressor(n_estimators = 10, random_state = 42)
X = emp_train[cols]
y = emp_train['is_promoted']
X_train, y_train = X,y
cols = ['department', 'region', 'education', 'gender', 'recruitment_channel', 'no_of_trainings', 'age', 'previous_year_rating', 'length_of_service', 'KPIs_met >80%', 'awards_won?', 'avg_training_score', 'training_scr_35_50', 'training_scr_50_65', 'training_scr_65_80', 'training_scr_85_100', 'age_18_25', 'age_25_35', 'age_35_45', 'age_45_60', 'age_training', 'KPI_training', 'education_age', 'region_max', 'len_serv_0_5', 'len_serv_5_10', 'len_serv_10_15', 'len_serv_15_20', 'len_serv_25']
X_test = emp_test[cols]
train_features = X_train
test_features = X_test
train_labels = y_train
#test_labels = y_test
base_model.fit(train_features, train_labels)

predictions = base_model.predict(test_features)

best_random = rf_random.best_estimator_
print(best_random)
y_pred = rf_random.predict(test_features)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
