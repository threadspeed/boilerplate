---
title: python script digit version charles dadi (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'digit version charles dadi'


Modules used in program: 
* `import pylab as pl`
* `import logging`
* `import timeit`

## python digit version charles dadi

Python mysql example: digit version charles dadi

```python
#http://scikit-learn.org/stable/auto_examples/applications/face_recognition.html#example-applications-face-recognition-py
from sklearn.ensemble import RandomForestClassifier
from numpy import genfromtxt, savetxt
from sklearn import neighbors, datasets

from sklearn.cross_validation import train_test_split
from sklearn.datasets import fetch_lfw_people
from sklearn.grid_search import GridSearchCV
from sklearn.metrics import classification_report
from sklearn.metrics import confusion_matrix
from sklearn.decomposition import RandomizedPCA
from sklearn import cross_validation
from sklearn.cross_validation import train_test_split
from sklearn.grid_search import GridSearchCV


from sklearn.ensemble import AdaBoostClassifier

from sklearn.decomposition import SparsePCA, MiniBatchSparsePCA

from sklearn.datasets import fetch_olivetti_faces
from sklearn.cluster import MiniBatchKMeans
from sklearn import decomposition

from sklearn.ensemble import RandomForestClassifier

from sklearn.svm import SVC
import timeit

start = timeit.default_timer() #// Starting time calculation
from time import time
import logging
import pylab as pl


train_path='/home/cerveau2charles/Dropbox/Ivan-Charles-Dan/digit recognizer/train.csv'
test_path='/home/cerveau2charles/Dropbox/Ivan-Charles-Dan/digit recognizer/test.csv'
submission_path='/home/cerveau2charles/Dropbox/Ivan-Charles-Dan/digit recognizer/'


#create the training & test sets, skipping the header row with [1:]
dataset = genfromtxt(open(train_path,'r'), delimiter=',', dtype='f8')[1:,:]    
target = [x[0] for x in dataset]
test = genfromtxt(open(test_path,'r'), delimiter=',', dtype='f8')[1:]
train=genfromtxt(open(train_path,'r'), delimiter=',', dtype='f8')[1:,1:]
    

n_components =100
    
    
#Dimension reduction .methods
estimators = [

    ('Eigenfaces - RandomizedPCA',
     decomposition.RandomizedPCA(n_components=n_components,iterated_power=20, whiten=True),
     True),

    ('Non-negative components - NMF',
     decomposition.NMF(n_components=n_components, init='nndsvda', beta=5.0,
                       tol=5e-3, sparseness='components'),
     False),

    ('Independent components - FastICA',
     decomposition.FastICA(n_components=n_components, whiten=True),
     True),

    ('Sparse comp. - MiniBatchSparsePCA',
     decomposition.MiniBatchSparsePCA(n_components=n_components, alpha=0.8,
                                      n_iter=100, batch_size=3),
     True),

    ('MiniBatchDictionaryLearning',
        decomposition.MiniBatchDictionaryLearning(n_components=15, alpha=0.1,
                                                  n_iter=50, batch_size=3),
     True),

    ('Cluster centers - MiniBatchKMeans',
        MiniBatchKMeans(n_clusters=n_components, tol=1e-3, batch_size=20,
                        max_iter=50),
     True),

    ('Factor Analysis components - FA',
     decomposition.FactorAnalysis(n_components=n_components, max_iter=2),
     True),
]    

    

which_pca = 0
print("Extracting the top %d %s..." % (n_components, estimators[which_pca][0]))
t0 = time()
pca=estimators[which_pca][1].fit(train)
train_time = (time() - t0)
print("done in %0.3fs" % train_time)

t0 = time()
train_pca = pca.transform(train)
test_pca = pca.transform(test)
print("done in %0.3fs" % (time() - t0))



################################################################################
# Grid search with k-fold cross validation to tune parameters for SVC

# parameters for SVC
# right way to tune SVC - 'A Practical Guide to SVC'
# loose search
# Results -- gamma=2**-5, C=2**5
# tuned_parameters = [{'kernel': ['rbf'],
#                      'gamma': [2**-15, 2**-11, 2**-7, 2**-5, 2**-3, 2**-1],
#                      'C': [2**-3, 2**-1, 2, 2**3, 2**5, 2**7, 2**9, 2**11, 2**13, 2**15]}]
# fine search
# tuned_parameters = [{'kernel': ['rbf'], 
#                      'gamma': [2**-9, 2**-8, 2**-7, 2**-6, 2**-5, 2**-4],
#                      'C': [2**3, 2**4, 2**5, 2**6, 2**7, 2**8, 2**9, 2**10]}]

# parameters for LinearSVC
# tuned_parameters = [{'loss': ['l2'],
#                      'penalty': ['l1', 'l2'],
#                      'C': [2**-3, 2**-1, 2, 2**3, 2**5, 2**7, 2**9, 2**11, 2**13, 2**15]}]

# parameters for Tree
# tuned_parameters = [{'max_depth': ['8', '10', '12', '15', '18'],
#                      'min_split': ['3', '4', '5', '6', '7', '8', '9']}]

# parameters for kNN



###############################################################################
# Train a SVM classification model
print("Fitting the classifier to the training set")
t0 = time()

              
tuned_parameters = [{'kernel': ['linear','rbf'], 
                      'gamma': [2**-5, 2**-4],
                      'C': [2**3, 2**4, 2**5, 2**6, 2**7, 2**8]}]
                      
clf = GridSearchCV(SVC(kernel='rbf', class_weight='auto'), tuned_parameters)
clf = clf.fit(train_pca, target)
print("done in %0.3fs" % (time() - t0))
print("Best estimator found by grid search:")
print(clf.best_estimator_)
savetxt(submission_path+'PCA'+estimators[which_pca][0]+'_SVM', clf.predict(test_pca), delimiter=',', fmt='%f')
print("done in %0.3fs" % (time() - t0))


###############################################################################
# Train a KNN classification model
print("Fitting the classifier to the training set")
t0 = time()
tuned_parameters = [{'n_neighbors': [5,6]}]
clf = GridSearchCV(neighbors.KNeighborsClassifier(n_neighbors=5), tuned_parameters, cv=3, n_jobs=-1).fit(train_pca, target)
print('Best parameters set found on development set:')
print(clf.best_estimator_)
savetxt(submission_path+ 'PCA'+estimators[which_pca][0]+'_KNN', clf.predict(test_pca), delimiter=',', fmt='%f')
print("done in %0.3fs" % (time() - t0))
###############################################################################




###############################################################################
#Train adaBoost Multi Class
clf = AdaBoostClassifier(n_estimators=100)
clf = clf.fit(train_pca, target)
print("done in %0.3fs" % (time() - t0))
savetxt(submission_path+'PCA'+estimators[which_pca][0]+'_AdaBoost', clf.predict(test_pca), delimiter=',', fmt='%f')
print("done in %0.3fs" % (time() - t0))

#create and train the random forest
#multi-core CPUs can use: rf = RandomForestClassifier(n_estimators=100, n_jobs=2) 
#rf = RandomForestClassifier(n_estimators=100)
#rf.fit(train, target)
#savetxt(submission_path+randomForest, rf.predict(test), delimiter=',', fmt='%f')

#n_neighbors = 5
#clf = neighbors.KNeighborsClassifier(n_neighbors)
#clf.fit(train, target)
#savetxt(submission_path+'knn', clf.predict(test), delimiter=',', fmt='%f')

###############################################################################
# Compute a randomized PCA (eigenfaces) on the face dataset (treated as unlabeled
# dataset): unsupervised feature extraction / dimensionality reduction
n_components = 33
print("Extracting the top %d eigenfaces from %d faces"
      % (n_components, size(train,0)))
t0 = time()
pca = RandomizedPCA(n_components=n_components, whiten=True).fit(train)
print("done in %0.3fs" % (time() - t0))
print("Projecting the input data on the eigenfaces orthonormal basis")
t0 = time()
train_pca = pca.transform(train)
test_pca = pca.transform(test)
print("done in %0.3fs" % (time() - t0))




    ###############################################################################
# Train a randomforestclassification model
print("Fitting the classifier to the training set")
t0 = time()
clf =  RandomForestClassifier(n_jobs=500)
clf.fit(train_pca, target)
print("done in %0.3fs" % (time() - t0))
savetxt(submission_path+'randomForest', clf.predict(test_pca), delimiter=',', fmt='%f')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
