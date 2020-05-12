---
title: python script RW%2520with%2520random%2520steps (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'RW%2520with%2520random%2520steps'

Functions in program: 
* `def dir(d):`

Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import random`
* `import numpy as np`

## python RW%2520with%2520random%2520steps

Python example: RW%2520with%2520random%2520steps

```python
import numpy as np
import random
import matplotlib.pyplot as plt


def dir(d):
    if d == 1:
        x = 1
    else:
        x = -1
    return x


M, N, l = 101, 1000, 1

rd = np.random.randint(2, size=(N, M))
for i in range(0, N):  # def direction
    for j in range(0, M):
        rd[i][j] = dir(rd[i][j])

X = np.zeros((N, M))
for i in range(0, N):
    for j in range(0, M):
        X[i][j] = X[i][j - 1] + random.random() * rd[i][j]

Y = [10,20,30,40,50,60,70,80,90,100]

tav=np.zeros((N,10))
eav=np.zeros(10)

for i in range (0,N):
    for j in range (0,len(Y)):
        for k in range (0,Y[j]):
            tav[i][j]=tav[i][j]+X[i][k]
for i in range (0,N):
    for j in range (0,len(Y)):
        tav[i][j]=(tav[i][j])/Y[j]
for j in range (0,len(Y)):
    for i in range (0,N):
        eav[j]+=eav[j]+tav[i][j]
    eav[j]=eav[j]/N

X2 = np.zeros((N + 2, M))

# calculate X**2
for i in range(0, N):
    for j in range(0, M):
        X2[i][j] = (X[i][j]) ** 2

# calculate <x**2>
for i in range(0, M):
    for j in range(0, N):
        X2[N][i] = X2[N][i] + X2[j][i]
    X2[N][i] = X2[N][i] / N

for i in range(0,M):
    X2[N+1][i]=(X2[N][i])**(1.1)

#print(eavx)
plt.plot(X2[N,:])
print(X2[N,:])
#plt.plot(X2[N,:])
plt.show()
plt.plot(X2[N+1,:])
plt.show()

#print(tavx[5,:])


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
