---
title: python script var-1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'var-1'

Functions in program: 
* `def kur(x,var,mean):`
* `def skew(x,var,mean):`

Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import numpy as np`

## python var-1

Python example: var-1

```python
import numpy as np
import matplotlib.pyplot as plt

def skew(x,var,mean):
    s3 = var**(3/2)
    m = np.zeros(len (x))
    for i in range(0,len(x)):
        m[i]=(x[i]-mean)**3
    m3 = np.mean(m)
    s = m3/s3
    return s
def kur(x,var,mean):
    s4 = var**(2)
    m = np.zeros(len (x))
    for i in range(0,len(x)):
        m[i]=(x[i]-mean)**4
    m4 = np.mean(m)
    k = m4/s4
    return k

x = np.random.normal(0,2,100000) #Normal Random
y = np.random.rand(1000000) #Uniform (0,1)

var_x = np.var(x)
mean_x = np.mean(x)
skew_x = skew(x,var_x,mean_x)
kur_x = kur(x,var_x,mean_x)
count, bins, ignored = plt.hist(x, 100, density=True,color='r',histtype = 'step')
plt.show()
print('x: ')
print('mean= ', mean_x,' var= ', var_x,' skew= ', skew_x, ' kur= ', kur_x)

var_y = np.var(y)
mean_y = np.mean(y)
skew_y = skew(y,var_y,mean_y)
kur_y = kur(y,var_y,mean_y)
count, bins, ignored = plt.hist(y, 100, density=True,color='r',histtype = 'step')
plt.show()
print('y: ')
print('mean= ', mean_y,' var= ', var_y,' skew= ', skew_y, ' kur= ', kur_y)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
