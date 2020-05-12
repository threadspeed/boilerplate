---
title: python script sklearn classifier (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sklearn classifier'


Modules used in program: 
* `import numpy as np`

## python sklearn classifier

Python mysql example: sklearn classifier

```python
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.datasets import make_moons, make_circles, make_classification
from sklearn.neural_network import MLPClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.svm import SVC
from sklearn.gaussian_process import GaussianProcessClassifier
from sklearn.gaussian_process.kernels import RBF
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier, AdaBoostClassifier
from sklearn.naive_bayes import GaussianNB
from sklearn.discriminant_analysis import QuadraticDiscriminantAnalysis

names = ["Nearest Neighbors", "Linear SVM", "RBF SVM", "Gaussian Process",
         "Decision Tree", "Random Forest", "Neural Net", "AdaBoost",
         "Naive Bayes", "QDA"]

classifiers = [
    KNeighborsClassifier(3),
    SVC(kernel="linear", C=0.025),
    SVC(gamma=2, C=1),
    GaussianProcessClassifier(1.0 * RBF(1.0)),
    DecisionTreeClassifier(max_depth=5),
    RandomForestClassifier(max_depth=5, n_estimators=10, max_features=1),
    MLPClassifier(alpha=1),
    AdaBoostClassifier(),
    GaussianNB(),
    QuadraticDiscriminantAnalysis()]

X_train = [[1,2,3], [1,1,1], [3,2,1], [1,3,1]]
y_train = [      1,       2,       3,       4]

X_test  = [[1.1,.9,1], [1,4,1]]
y_test  = [         2,       4]

for name, clf in zip(names, classifiers):
    try:
        print("%s:"%name)
        clf.fit(X_train, y_train)
        print(clf.score(X_test, y_test))
        print(clf.predict(X_train), y_train)
        print(clf.predict(X_test), y_test)
        print(zip(clf.classes_, clf.predict_proba(X_test)[0]);)
    except:
        pass








'''print(__doc__)



import numpy as np

from matplotlib.colors import ListedColormap
from sklearn.model_selection import train_test_split
from sklearn.preprocessing import StandardScaler
from sklearn.datasets import make_moons, make_circles, make_classification
from sklearn.neural_network import MLPClassifier
from sklearn.neighbors import KNeighborsClassifier
from sklearn.svm import SVC
from sklearn.gaussian_process import GaussianProcessClassifier
from sklearn.gaussian_process.kernels import RBF
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier, AdaBoostClassifier
from sklearn.naive_bayes import GaussianNB
from sklearn.discriminant_analysis import QuadraticDiscriminantAnalysis


h = .02  # step size in the mesh

names = ["Nearest Neighbors", "Linear SVM", "RBF SVM", "Gaussian Process",
         "Decision Tree", "Random Forest", "Neural Net", "AdaBoost",
         "Naive Bayes", "QDA"]

classifiers = [
    KNeighborsClassifier(3),
    SVC(kernel="linear", C=0.025),
    SVC(gamma=2, C=1),
    GaussianProcessClassifier(1.0 * RBF(1.0)),
    DecisionTreeClassifier(max_depth=5),
    RandomForestClassifier(max_depth=5, n_estimators=10, max_features=1),
    MLPClassifier(alpha=1),
    AdaBoostClassifier(),
    GaussianNB(),
    QuadraticDiscriminantAnalysis()]

ds=(np.array([[1,2,.5],[1.1,1.9,1],[1,2.1,0],[.9,2,.5],[1.1,2.1,1],[2,1,0],[1.9,.9,.5],[2.1,1.1,1],[1.9,1.1,0],[2.1,.9,.5]]),np.array([1,1,1,1,1,0,0,0,0,1]))

X, y = ds
X = StandardScaler().fit_transform(X)
X_train, X_test, y_train, y_test = \
    train_test_split(X, y, test_size=.4, random_state=42)

print(X_train)
print(X_test)


# iterate over classifiers
for name, clf in zip(names, classifiers):

    print(X_train, y_train)
    clf.fit(X_train, y_train)
    #score = clf.score(X_test, y_test)
    print(clf.predict(X_test);)
    print(clf.predict(X_train);)
    print(clf.predict([[1,1,1]]);)
    clf.fit(X_test, y_test)
    #score = clf.score(X_test, y_test)
    print(clf.predict(X_test);)
    print(clf.predict(X_train);)
    print(clf.predict([[1,1,1]]);)

    #print(name+": "+str(score)''')




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
