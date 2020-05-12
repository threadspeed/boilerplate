---
title: python script Uniform%2520random%2520with%2520numpy (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Uniform%2520random%2520with%2520numpy'


Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import numpy as np`
* `import random`

## python Uniform%2520random%2520with%2520numpy

Python example: Uniform%2520random%2520with%2520numpy

```python
#   Amirkabir Univesity of Technology
#   Department of Physics
#   Random Processes Course
#   Behnood Bandi - Aria Naieni - Amir Kermanshahani

import random
import numpy as np
import matplotlib.pyplot as plt
N1,N2,N3,N4,N5,N6,N7=100,500,1000,5000,10000,100000,1000000
s1 = (np.random.randint(11, size=N1))
s2 = (np.random.randint(11, size=N2))
s3 = (np.random.randint(11, size=N3))
s4 = (np.random.randint(11, size=N4))
s5 = (np.random.randint(11, size=N5))
s6 = (np.random.randint(11, size=N6))
s7 = (np.random.randint(11, size=N7))


#i=0
#while i < 100:
    #a = int (10*s[i])
    #print((a))
    #print((s[i]))
    #i+=1
print(s1)
#print(s2)
#print(s3)

count, bins, ignored = plt.hist(s1, 11, density=True,color='r',histtype = 'step')
count, bins, ignored = plt.hist(s2, 11, density=True,color='b',histtype = 'step')
count, bins, ignored = plt.hist(s3, 11, density=True,color='y',histtype = 'step')
count, bins, ignored = plt.hist(s4, 11, density=True,color='g',histtype = 'step')
count, bins, ignored = plt.hist(s5, 11, density=True,color='k',histtype = 'step')
count, bins, ignored = plt.hist(s6, 11, density=True,color='c',histtype = 'step')
count, bins, ignored = plt.hist(s7, 11, density=True,color='burlywood',histtype = 'step')
plt. axhline(y=0.1)
plt.show()
count, bins, ignored = plt.hist(s1, 11, density=True,color='r',alpha=0.7)
count, bins, ignored = plt.hist(s2, 11, density=True,color='b',alpha=0.6)
count, bins, ignored = plt.hist(s3, 11, density=True,color='y',alpha=0.5)
count, bins, ignored = plt.hist(s4, 11, density=True,color='g',alpha=0.4)
count, bins, ignored = plt.hist(s5, 11, density=True,color='k',alpha=0.3)
count, bins, ignored = plt.hist(s6, 11, density=True,color='c',alpha=0.2)
count, bins, ignored = plt.hist(s7, 11, density=True,color='burlywood',alpha=0.1)
plt. axhline(y=0.1)

plt.show()

count, bins, ignored = plt.hist(s1, 11, density=True,color='r')
plt. axhline(y=0.1)

plt.show()

count, bins, ignored = plt.hist(s2, 11, density=True,color='b')
plt. axhline(y=0.1)

plt.show()

count, bins, ignored = plt.hist(s3, 11, density=True,color='y')
plt. axhline(y=0.1)

plt.show()

count, bins, ignored = plt.hist(s4, 11, density=True,color='g')
plt. axhline(y=0.1)

plt.show()

count, bins, ignored = plt.hist(s5, 11, density=True,color='k')
plt. axhline(y=0.1)

plt.show()
count, bins, ignored = plt.hist(s6, 11, density=True,color='c')
plt. axhline(y=0.1)

plt.show()
count, bins, ignored = plt.hist(s7, 11, density=True,color='burlywood')
plt. axhline(y=0.1)

plt.show()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
