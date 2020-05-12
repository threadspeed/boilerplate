---
title: python script rect (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rect'

Functions in program: 
* `def any( max_loop = 10000000 ):`
* `def upleft( max_loop = 10000000 ):`

Modules used in program: 
* `import sys`
* `import random`

## python rect

Python example: rect

```python
import random
import sys

def upleft( max_loop = 10000000 ):
    sample_count = 0
    true_count = 0
    while sample_count < max_loop:
        tuxaia = [ (random.random(), random.random()) for i in range(0,8) ]
        sample_count += 1
        kappa_cancer = [ i[0]//0.25 == 3.0 and i[1]//0.25 == 0.0 for i in tuxaia[0:3] ]
        if kappa_cancer.count(False) > 0:
            kappa_norm = [ i[0]//0.25 == 3.0 and i[1]//0.25 == 0.0 for i in tuxaia[3:8] ]
            if (kappa_norm.count(True) > 0) == False:
                true_count += 1
    return true_count/max_loop

def any( max_loop = 10000000 ):
    sample_count = 0
    true_count = 0
    while sample_count < max_loop:
        tuxaia = [ (random.random(), random.random()) for i in range(0,8) ]
        sample_count += 1
        tuxaioX = tuxaia[0][0]//0.25
        tuxaioY = tuxaia[0][1]//0.25
        kappa_cancer = [ i[0]//0.25 == tuxaioX and i[1]//0.25 == tuxaioY for i in tuxaia[1:3] ]
        if kappa_cancer.count(False) > 0:
            kappa_norm = [ i[0]//0.25 == tuxaioX and i[1]//0.25 == tuxaioY for i in tuxaia[3:8] ]
            if (kappa_norm.count(True) > 0) == False:
                true_count += 1
    return true_count/max_loop

repeats = int(sys.argv[1])
location = sys.argv[2]
if location == 'UPLEFT':
    output = upleft(repeats)
elif location == 'ANY':
    output = any(repeats)
else:
    sys.stderr.write( "2nd argument should be <ANY> or <UPLEFT>" )
    sys.exit(1)

with open('results.txt', 'w') as f:
 f.write('{}'.format(output))
 f.write('\n')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
