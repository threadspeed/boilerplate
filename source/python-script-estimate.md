---
title: python script estimate (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'estimate'


Modules used in program: 
* `import sys,collections`
* `import sklearn`

## python estimate

Python mysql example: estimate

```python
import sklearn
from sklearn.ensemble import RandomForestClassifier
from sklearn.lda import LDA
from sklearn.linear_model import SGDClassifier
import sys,collections

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

    agents[myid]['fs'].append([gs])
    agents[myid]['ts'].append(menu)

f.close()


##estimate conf
cutoffs = {}
for myid in agents:
    agent = agents[myid]
    gs_max = 0
    gdict = {}

    for i in range(len(agent['fs'])):
        gs = agent['fs'][i][0]
        menu = agent['ts'][i]

        if gs not in gdict:
            gdict[gs] = []
        
        gdict[gs].append(menu)

        if gs_max < gs:
            gs_max = gs


    cutoff = 100

    for i in range (3, gs_max+1):


        if i in gdict:
            counter = collections.Counter(gdict[i])
            pairs =  counter.most_common()
            #flatness = 1.0 - float(max(counter.values())-min(counter.values())) / float(len(gdict[i]))
            flatness = 1.0 - (float(max(counter.values())) / float(len(gdict[i])))
        else:
            flatness = 0.0

        if flatness > 0.3:
            cutoff = i+1
            break

    print(myid, str(cutoff/10.0), agent['conf'])
    cutoffs[myid] = cutoff

#sys.exit()

##reread data
f = open("../GenData/train.txt","r")
for line in f:
    data = line.split()
    myid = int(data[0])
    gs = int(data[1])
    menu = data[2].strip()

    if gs <= cutoffs[myid]:
        agents[myid]['fs'].append([gs])
        agents[myid]['ts'].append(menu)

f.close()
 

#    for gs in range(1,gs_max+1):

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
