---
title: python script normal%2520rand (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'normal%2520rand'


Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import random`

## python normal%2520rand

Python example: normal%2520rand

```python
import random
import numpy as np
import matplotlib.pyplot as plt
mu, sigma = 0 ,1 # mean and standard deviation
N1,N2,N3,N4,N5,N6=100,500,1000,5000,10000,100000
s1 = (np.random.normal(mu, sigma, N1))
s2 = (np.random.normal(mu, sigma, N2))
s3 = (np.random.normal(mu, sigma, N3))
s4 = (np.random.normal(mu, sigma, N4))
s5 = (np.random.normal(mu, sigma, N5))
s6 = (np.random.normal(mu, sigma, N6))

#i=0
#while i < 100:
    #a = int (10*s[i])
    #print((a))
    #print((s[i]))
    #i+=1
#print(s1)
#print(s2)
#print(s3)

count, bins, ignored = plt.hist(s1, 30, density=True,color='r',histtype = 'step')
count, bins, ignored = plt.hist(s2, 30, density=True,color='b',histtype = 'step')
count, bins, ignored = plt.hist(s3, 30, density=True,color='y',histtype = 'step')
count, bins, ignored = plt.hist(s4, 30, density=True,color='g',histtype = 'step')
count, bins, ignored = plt.hist(s5, 30, density=True,color='k',histtype = 'step')
count, bins, ignored = plt.hist(s6, 30, density=True,color='c',histtype = 'step')
plt.plot(bins, 1/(sigma * np.sqrt(2 * np.pi)) *
               np.exp( - (bins - mu)**2 / (2 * sigma**2) ),
         linewidth=2, color='m')
plt.show()
count, bins, ignored = plt.hist(s1, 30, density=True,color='r',alpha=0.7)
count, bins, ignored = plt.hist(s2, 30, density=True,color='b',alpha=0.6)
count, bins, ignored = plt.hist(s3, 30, density=True,color='y',alpha=0.5)
count, bins, ignored = plt.hist(s4, 30, density=True,color='g',alpha=0.4)
count, bins, ignored = plt.hist(s5, 30, density=True,color='k',alpha=0.3)
count, bins, ignored = plt.hist(s6, 30, density=True,color='c',alpha=0.2)
plt.plot(bins, 1/(sigma * np.sqrt(2 * np.pi)) *
               np.exp( - (bins - mu)**2 / (2 * sigma**2) ),
         linewidth=2, color='m')
plt.show()


count, bins, ignored = plt.hist(s1, 30, density=True,color='r')
plt.plot(bins, 1/(sigma * np.sqrt(2 * np.pi)) *
               np.exp( - (bins - mu)**2 / (2 * sigma**2) ),
         linewidth=2, color='m')
plt.show()

count, bins, ignored = plt.hist(s2, 30, density=True,color='b')
plt.plot(bins, 1/(sigma * np.sqrt(2 * np.pi)) *
               np.exp( - (bins - mu)**2 / (2 * sigma**2) ),
         linewidth=2, color='m')
plt.show()

count, bins, ignored = plt.hist(s3, 30, density=True,color='y')
plt.plot(bins, 1/(sigma * np.sqrt(2 * np.pi)) *
               np.exp( - (bins - mu)**2 / (2 * sigma**2) ),
         linewidth=2, color='m')
plt.show()

count, bins, ignored = plt.hist(s4, 30, density=True,color='g')
plt.plot(bins, 1/(sigma * np.sqrt(2 * np.pi)) *
               np.exp( - (bins - mu)**2 / (2 * sigma**2) ),
         linewidth=2, color='m')
plt.show()

count, bins, ignored = plt.hist(s5, 30, density=True,color='k')
plt.plot(bins, 1/(sigma * np.sqrt(2 * np.pi)) *
               np.exp( - (bins - mu)**2 / (2 * sigma**2) ),
         linewidth=2, color='m')
plt.show()
count, bins, ignored = plt.hist(s6, 30, density=True,color='c')
plt.plot(bins, 1/(sigma * np.sqrt(2 * np.pi)) *
               np.exp( - (bins - mu)**2 / (2 * sigma**2) ),
         linewidth=2, color='m')
plt.show()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
