---
title: python script parallel dummy (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'parallel dummy'

Functions in program: 
* `def executeParallel(fun, joblist, n_jobs=5):`
* `def remote_exec(f, idcpu, fun=None):`
* `def splitMe(df, n=20, prefix=''):`
* `def randStr(N=10):`
* `def chunks(l, n):`

Modules used in program: 
* `import string`
* `import random`
* `import functools`

## python parallel dummy

Python example: parallel dummy

```python
from IPython.parallel import Client
from sklearn.externals import joblib
import functools
from joblib import Parallel, delayed
import random
import string

TMPDIR = '/tmp'

def chunks(l, n):
    """Yield successive n-sized chunks from l."""
    for i in xrange(0, len(l), n):
        yield l[i:i+n]

def randStr(N=10):
    return ''.join(random.SystemRandom().choice(string.ascii_uppercase + string.digits) for _ in range(N))

# Split function
def splitMe(df, n=20, prefix=''):
    result = []
    idcpu=0
    for l in chunks(range(df.shape[1]), n):
        filename = '%s/parallelgen_%d_%d_%d_%s_%s' %(TMPDIR, idcpu, l[0], l[-1], prefix, randStr())
        cols = [df.columns[i] for i in l]
        joblib.dump(df[cols], filename)
        result.append((idcpu,filename))
        idcpu=idcpu+1
    return result
 
# Remote execution function
def remote_exec(f, idcpu, fun=None):
    from sklearn.externals import joblib
    df = joblib.load(f)
    return fun(df, idcpu)
 
# parallel function to call
def executeParallel(fun, joblist, n_jobs=5):
    return Parallel(n_jobs=n_jobs)(delayed(remote_exec)(f, idcpu, fun=fun) for (idcpu, f) in joblist)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
