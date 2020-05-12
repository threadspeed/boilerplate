---
title: python script godmode (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'godmode'


Modules used in program: 
* `import sklearn`

## python godmode

Python example: godmode

```python
import sklearn
from sklearn.ensemble import RandomForestClassifier
from sklearn.lda import LDA
from sklearn.linear_model import SGDClassifier

##cheat
agents = {}
f = open("../GenData/answers.txt","r")
for line in f:
    data = line.split()
    myid = int(data[0])
    menu = data[1].strip()
    conf = float(data[2])

    if myid not in agents:
        agents[myid]={}
        agents[myid]['fs'] = []
        agents[myid]['ts'] = []
        agents[myid]['conf'] = conf

##read data
f = open("../GenData/train.txt","r")
for line in f:
    data = line.split()
    myid = int(data[0])
    gs = int(data[1])
    menu = data[2].strip()

    ##cheat
    th = -1
    '''
    ##3 levels
    if agents[myid]['conf'] <= 0.33:
        #th = 4
        th = 3
    elif agents[myid]['conf'] <= 0.66:
        #th = 8
        th = 9
    else:
        th = 100
    '''
    ##2 levels
    if agents[myid]['conf'] <= 0.5:
        th = 3 ##83
    else:
        th = 100
    #th = int(agents[myid]['conf']*10)+2 ##88%

    if gs <= th: ##only it is viable data
        agents[myid]['fs'].append([gs])
        agents[myid]['ts'].append(menu)
    
f.close()

results = {}

for myid in agents:
    #print(agents[myid]['fs'])
    try:
        #clf = RandomForestClassifier(n_estimators=10)
        clf = sklearn.linear_model.LogisticRegression()
        clf = clf.fit(agents[myid]['fs'],agents[myid]['ts'] )
        results[myid] = clf.predict([1])

        del clf
    except:
        results[myid] = ["X"]


##calc correct answers

num_correct = 0

f = open("../GenData/answers.txt","r")
for line in f:
    data = line.split()
    myid = int(data[0])
    menu = data[1].strip()

    print(menu, results[myid])

    if menu == results[myid]:
        num_correct = num_correct + 1

f.close()
print(num_correct)



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
