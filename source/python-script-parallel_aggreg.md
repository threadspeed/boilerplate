---
title: python script parallel aggreg (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'parallel aggreg'

Functions in program: 
* `def executeParallel(fun, joblist, id_uniq, n_jobs=10):`
* `def remote_exec(f, id_uniq, fun=None):`
* `def splitMe(df, id_uniq, n=100, prefix=''):`
* `def randStr(N=10):`

Modules used in program: 
* `import string`
* `import random`
* `import functools`

## python parallel aggreg

Python example: parallel aggreg

```python
from IPython.parallel import Client
from sklearn.externals import joblib
import functools
from joblib import Parallel, delayed
import random
import string

TMPDIR = '/tmp'

def randStr(N=10):
    return ''.join(random.SystemRandom().choice(string.ascii_uppercase + string.digits) for _ in range(N))
    
# Split function
def splitMe(df, id_uniq, n=100, prefix=''):
    result = []
    stratifiedIdUniqList = {}
    for j in range(n):
        stratifiedIdUniqList[j] = []
    i=0
    for nc, val in df[id_uniq].value_counts().iteritems():
        stratifiedIdUniqList[i].append(nc)
        i=(i+1)%n
    for idcpu, ncl in stratifiedIdUniqList.iteritems():
        filename = '%s/parallelgen_%d_%s_%s_%s' %(TMPDIR, idcpu, id_uniq, prefix, randStr())
        joblib.dump(df[df[id_uniq].isin(ncl)], filename, compress=2)
        result.append(filename)
    return result

# Remote execution function
def remote_exec(f, id_uniq, fun=None):
    from sklearn.externals import joblib
    dfgb = joblib.load(f).groupby(id_uniq)
    return fun(dfgb)

# parallel function to call 
def executeParallel(fun, joblist, id_uniq, n_jobs=10):
    return Parallel(n_jobs=n_jobs)(delayed(remote_exec)(f, id_uniq, fun=fun) for f in joblist)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
