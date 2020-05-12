---
title: python script CT10 1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'CT10 1'

Functions in program: 
* `def hasher(bodies, N):`
* `def plot_confusion_matrix(cm, classes,`

Modules used in program: 
* `import json`
* `import itertools`
* `import matplotlib.pyplot as plt`
* `import numpy as np`

## python CT10 1

Python example: CT10 1

```python
import numpy as np
import matplotlib.pyplot as plt
import itertools

def plot_confusion_matrix(cm, classes,
                          normalize=False,
                          title='Confusion matrix',
                          cmap=plt.cm.Blues):
    """
    This function prints and plots the confusion matrix.
    """
    plt.imshow(cm, interpolation='nearest', cmap=cmap)
    plt.title(title)
    plt.colorbar()
    tick_marks = np.arange(len(classes))
    plt.xticks(tick_marks, classes, rotation=45)
    plt.yticks(tick_marks, classes)

    fmt = '.2f' if normalize else 'd'
    thresh = cm.max() / 2.
    for i, j in itertools.product(range(cm.shape[0]), range(cm.shape[1])):
        plt.text(j, i, format(cm[i, j], fmt),
                 horizontalalignment="center",
                 color="white" if cm[i, j] > thresh else "black")

    plt.tight_layout()
    plt.ylabel('True label')
    plt.xlabel('Predicted label')
    plt.show()


import json
from sklearn.feature_extraction.text import CountVectorizer

path = 'reuters_merged.json'

j_text = json.load(open(path))

article_bodies = []
article_topics = []
for article in j_text:
# Here we sort the articles with no body or topics away from the real ones.
    try:
        body = article['body']
        topics = article['topics']
        
        article_bodies.append(body)
        if 'earn' in topics:
            article_topics.append('earn')
        else:
            article_topics.append('not earn')
    except:
        continue
            

# BAG OF WORDS
vectorizer = CountVectorizer()
M = vectorizer.fit_transform(article_bodies)

# RANDOM FOREST CLASSIFIER WITH BAG OF WORDS
from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(M, article_topics, train_size=0.8)


from sklearn.ensemble import RandomForestClassifier
clf = RandomForestClassifier(n_estimators=50)
clf = clf.fit(X_train, y_train)

# ACCURACY
from sklearn.metrics import accuracy_score, confusion_matrix

y_predict = clf.predict(X_test)
acc = accuracy_score(y_test, y_predict)
print('Accuracy with BoW: %.2f,' % (acc*100), 'with matrix shape', M.shape)

cm = confusion_matrix(y_test, y_predict, labels=['earn', 'not earn'])
plot_confusion_matrix(cm, ['earn', 'not earn'], title="Confusion Matrix w/ BoW")

# RANDOM FOREST CLASSIFIER WITH HASHING
def hasher(bodies, N):
    hash_values = []
    for b in bodies:
        hashs = [0]*N
        words_in_body = b.split(" ")
        for w in words_in_body:
            h = hash(w)
            hashs[h % N] += 1
                
        hash_values.append(hashs)
                
    return hash_values

M1 = hasher(article_bodies, 1000)

from sklearn.model_selection import train_test_split
X_train, X_test, y_train, y_test = train_test_split(M1, article_topics, train_size=0.8)


from sklearn.ensemble import RandomForestClassifier
clf = RandomForestClassifier(n_estimators=50)
clf = clf.fit(X_train, y_train)

# ACCURACY
y_predict = clf.predict(X_test)
acc = accuracy_score(y_test, y_predict)


cm = confusion_matrix(y_test, y_predict, labels=['earn', 'not earn'])
print('Accuracy with hashing: %.2f,' % (acc*100), 'with matrix shape (%d, %d)' % (len(M1), len(M1[1])))
plot_confusion_matrix(cm, ['earn', 'not earn'], title="Confusion Matrix w/ Hashing")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
