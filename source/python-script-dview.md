---
title: python script dview (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dview'

Functions in program: 
* `def toktok_f(f):`
* `def toktok(s):`
* `def splitMe(df, n=20, prefix=''):`
* `def randStr(N=10):`
* `def chunks(l, n):`

Modules used in program: 
* `import string`
* `import random`

## python dview

Python example: dview

```python
# launch an IPython cluster using cli or ipython notebook interface

from IPython.parallel import Client
c = Client()
dview = c[:]
lview = c.load_balanced_view()

from sklearn.externals import joblib
import random
import string

TMPDIR = '/tmp'

def chunks(l, n):
    """Yield successive n-sized chunks from l."""
    for i in xrange(0, len(l), n):
        yield l[i:i+n]
        
def randStr(N=10):
    return ''.join(random.SystemRandom().choice(string.ascii_uppercase + string.digits) for _ in range(N))
     
def splitMe(df, n=20, prefix=''):
    result = []
    idcpu=0
    for l in chunks(range(df.shape[0]), n):
        filename = '%s/parallelgen_%d_%d_%d_%s_%s' %(TMPDIR, idcpu, l[0], l[-1], prefix, randStr())
        joblib.dump(df.ix[l], filename)
        result.append((idcpu,filename))
        idcpu=idcpu+1
    return result

def toktok(s):
  return s

def toktok_f(f):
    from sklearn.externals import joblib
    
    df = joblib.load(f[1])
    return df.acolumn.map(toktok)
    
dview['df'] = df
dview['toktok'] = toktok

lview.block = False
result_async = lview.map(toktok_f, splitMe(df, n=df.shape[0]/16))

## waiting for async computation ...
if result_async.ready():
  r_toktok = pd.concat(result_async.result(), axis=0)
  df['acolumns_tok'] = r_toktok


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
