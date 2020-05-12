---
title: python script stack overflow question 57802238 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'stack overflow question 57802238'

Functions in program: 
* `def feature_selection_and_engineering(df, encoder=None):`
* `def one_hot_encode(df, categorical_columns, encoder):`
* `def get_categorical_columns(df):`
* `def train_one_hot_encoder(df, categorical_columns):`
* `def remove_nan(df):`

Modules used in program: 
* `import pandas as pd`

## python stack overflow question 57802238

Python mysql example: stack overflow question 57802238

```python
import pandas as pd
from sklearn.ensemble import RandomForestClassifier
from sklearn.feature_selection import SelectFromModel
from sklearn.model_selection import train_test_split
from sklearn.ensemble import RandomForestRegressor
from sklearn.preprocessing import OneHotEncoder

train = pd.read_csv("https://raw.githubusercontent.com/oo92/Boston-Kaggle/master/train.csv")
test = pd.read_csv("https://raw.githubusercontent.com/oo92/Boston-Kaggle/master/test.csv")

# Iterates through the columns and fixes any NaNs
def remove_nan(df):
    replace_dict = {}
    for col in df.columns:
        # If there are any NaN values in this column
        if pd.isna(df[col]).any():
            # Replace NaN in object columns with 'N/A'
            if df[col].dtypes == 'object':
                replace_dict[col] = 'N/A'
            # Replace NaN in float columns with 0
            elif df[col].dtypes == 'float64':
                replace_dict[col] = 0
    df = df.fillna(replace_dict)
    return df

# Fits an sklearn one hot encoder
def train_one_hot_encoder(df, categorical_columns):
    # take one-hot encoding of categorical columns
    categorical_df = df[categorical_columns]
    enc = OneHotEncoder(sparse=False, handle_unknown='ignore')
    return enc.fit(categorical_df)

# Returns a list of categorical columns
def get_categorical_columns(df):
    categorical_columns = []
    for col in df.columns:
        # If column is not an int, add it to list of categorical columns
        if not(df[col].dtypes == 'float64' or df[col].dtypes == 'int64'):
            categorical_columns.append(col)
    
    return categorical_columns

# One hot encodes the given dataframe
def one_hot_encode(df, categorical_columns, encoder):
    # Get dataframe with only categorical columns
    categorical_df = df[categorical_columns]
    # Get one hot encoding
    ohe_df = pd.DataFrame(encoder.transform(categorical_df), columns=encoder.get_feature_names())
    # Get float columns
    float_df = df.drop(categorical_columns, axis=1)
    # Return the combined array
    return pd.concat([float_df, ohe_df], axis=1)

# Transforms a dataset to be ready for input into a model
def feature_selection_and_engineering(df, encoder=None):
    df = remove_nan(df)
    categorical_columns = get_categorical_columns(df)
    # If there is no encoder, train one
    if encoder == None:
        encoder = train_one_hot_encoder(df, categorical_columns)
    # Encode Data
    df = one_hot_encode(df, categorical_columns, encoder)
    # Return the encoded data AND encoder
    return df, encoder

# Save labels and drop from training data
labels = train['SalePrice']
train.drop('SalePrice', axis=1, inplace=True)

# Dividing the training dataset into train/test sets with the test size being 20% of the overall dataset.
x_train, x_test, y_train, y_test = train_test_split(train, labels, test_size = 0.2, random_state = 42)

# Reset indices after splitting
x_train.reset_index(drop=True, inplace=True)
x_test.reset_index(drop=True, inplace=True)
y_train.reset_index(drop=True, inplace=True)
y_test.reset_index(drop=True, inplace=True)

# Encode train and save encoder
x_train, encoder = feature_selection_and_engineering(x_train)

randomForestRegressor = RandomForestRegressor(n_estimators=1000)

# Invoking the Random Forest Classifier with a 1.25x the mean threshold to select correlating features
sel = SelectFromModel(RandomForestClassifier(n_estimators = 100), threshold = '1.25*mean')
sel.fit(x_train, y_train)

selected = sel.get_support()

# linearRegression.fit(x_train, y_train)
randomForestRegressor.fit(x_train, y_train)

# Transform the split test set using the same encoder
x_test, _ = feature_selection_and_engineering(x_test, encoder)

# Save the r^2 value of the model on training and test
train_r_squared = randomForestRegressor.score(x_train, y_train)
test_r_squared = randomForestRegressor.score(x_test, y_test)

# Transform the final test set using the same encoder
test, _ = feature_selection_and_engineering(test, encoder)

# Predicting for the data in the test set
predictions = randomForestRegressor.predict(test)

# Writing the predictions to a new CSV file
submission = pd.DataFrame({'Id': test['Id'], 'SalePrice': predictions})
filename = 'Boston-Submission.csv'
submission.to_csv(filename, index=False)

print("Training R Squared", train_r_squared)
print("Testing R Squared ", test_r_squared)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
