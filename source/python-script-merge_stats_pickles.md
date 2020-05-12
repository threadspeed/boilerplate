---
title: python script merge stats pickles (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'merge stats pickles'

Functions in program: 
* `def filename(N=10):`

Modules used in program: 
* `import string`
* `import random`
* `import argparse`
* `import pandas as pd`

## python merge stats pickles

Python example: merge stats pickles

```python
import pandas as pd
import argparse
import random
import string

def filename(N=10):
    return ''.join(random.choice(string.ascii_uppercase + string.digits) for _ in range(N))

parser = argparse.ArgumentParser(description='Merge token frequency pickles.')
parser.add_argument('paths', metavar='paths', nargs='+',
                   help='Paths of DF pickles')
parser.add_argument('--outpath', type=str, default='pickles2',
                   help='Where to save the combined DF pickle')
parser.add_argument('--min-pf', type=int, default=1,
                   help='Filter any terms that occur on fewer than a specified number of pages.')
parser.add_argument('--min-bf', type=int, default=1,
                   help='Filter any terms that occur in fewer than a specified number of books.')

args = parser.parse_args()

dfs = []
for path in args.paths:
    try:
        dfs.append(pd.read_pickle(path))
    except:
        print("error with %s" % path)
df = pd.concat(dfs).groupby(['token'], level=0).sum()

if args.min_pf > 1:
    df = df[df['PF'] >= args.min_pf]

if args.min_bf > 1:
    df = df[df['BF'] >= args.min_pf]

df.to_pickle("%s/%s.pickle" % (args.outpath, filename()))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
