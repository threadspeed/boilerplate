---
title: python script fishpool color prediction (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'fishpool color prediction'

Functions in program: 
* `def eval_metric(classifier, x_test, y_test):`
* `def nfold_split(x, y, n):`
* `def split_data(x, y, n):`
* `def load_data(file_path, col_type):`

Modules used in program: 
* `import random`

## python fishpool color prediction

Python example: fishpool color prediction

```python
from sklearn.ensemble import RandomForestClassifier
from sklearn.tree import DecisionTreeClassifier, DecisionTreeRegressor
from sklearn.linear_model import LogisticRegression
from sklearn.metrics import f1_score, precision_score, recall_score
import random

def load_data(file_path, col_type):
    x, y = list(), list()
    with open(file_path, 'r', encoding='UTF-8') as fin:
        fin.readline()
        for line in fin:
            line = line.strip().split(',')
            xx, yy = list(), 0
            try:
                for i, t in enumerate(col_type):
                    if t == 0: continue
                    elif t == 1:
                        xx.append(float(line[i]))
                    elif t == 2:
                        yy = int(line[i])
            except: continue
            x.append(xx)
            y.append(yy)
    return x, y

def split_data(x, y, n):
    return x[:n], y[:n], x[n:], y[n:]

def nfold_split(x, y, n):
    fold = len(x) // n
    for i in range(n):
        print('%d/%d Fold' % (i+1, n))
        a = i * fold
        b = (i + 1) * fold
        x_test = x[a:b]
        y_test = y[a:b]
        x_train = x[:a] + x[b:]
        y_train = y[:a] + y[b:]
        print('%4d Size of Train' % len(y_train), end='\t')
        print('%4d Positive in Train' % y_train.count(1))
        print('%4d Size of Test' % len(y_test), end='\t')
        print('%4d Positive in Test' % y_test.count(1))
        yield x_train, y_train, x_test, y_test

def eval_metric(classifier, x_test, y_test):
    y_pred = classifier.predict(x_test)

    TP, FP, FN, TN = 0, 0, 0, 0
    for i, yp in enumerate(y_pred):
        yt = y_test[i]
        if yp == yt and yt: TP += 1
        elif not yt: TN += 1
        elif yp: FP += 1
        else: FN += 1
    Epsilon = 0.000001
    Accuracy = (TP + TN) / (TP + FP + FN + TN)
    Precision = TP / (TP + FP + Epsilon)
    Recall = TP / (TP + FN + Epsilon)
    F1_Score = 2 * (Recall * Precision) / (Recall + Precision + Epsilon)
    print("Accuracy\t%.3f" % Accuracy)
    print("Precision\t%.3f" % Precision)
    print("Recall\t\t%.3f" % Recall)
    print("F1-Score\t%.3f\n" % F1_Score)

if __name__ == '__main__':
    # Set column type, 0 for drop, 1 for feature, 2 for label.
    # 0     1     2     3     4     5     6   7   8    9   10         11         12
    # 日期, 餵料, 排水, 水色, 水溫, 鹽度, PH, DO, NO2, 氨, 水利淨(g), 美速添(g), 活動觀察
    #           0  1  2  3  4  5  6  7  8  9  10 11 12
    col_type = [0, 1, 1, 2, 1, 1, 1, 0, 0, 1, 0, 0, 0]
    x, y = load_data('./data2.csv', col_type)

    # Shuffle data
    c = list(zip(x, y))
    random.shuffle(c)
    x, y = zip(*c)

    # 5-Fold Validation
    for x_train, y_train, x_test, y_test in nfold_split(x, y, 5):
        # Random Forest
        print('Random Forest')
        RFC = RandomForestClassifier(criterion='entropy', n_estimators=10, n_jobs=2)
        RFC = RFC.fit(x_train, y_train)
        eval_metric(RFC, x_test, y_test)

        # Decision Tree
        print('Decision Tree')
        DTC = DecisionTreeClassifier()
        DTC = DTC.fit(x_train, y_train)
        eval_metric(DTC, x_test, y_test)

        # Decision Tree Regressor
        print('Decision Tree Regressor')
        DTR = DecisionTreeRegressor()
        DTR = DTR.fit(x_train, y_train)
        eval_metric(DTR, x_test, y_test)

        # Logistic Regression
        print('Logistic Regression')
        LR = LogisticRegression(solver="lbfgs")
        LR = LR.fit(x_train, y_train)
        eval_metric(LR, x_test, y_test)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
