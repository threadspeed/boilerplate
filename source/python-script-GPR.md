---
title: python script GPR (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'GPR'

Functions in program: 
* `def shuffle(X, y):`
* `def partition_K(K, p=5):`
* `def partition(X, y, p=5):`
* `def K_inv_y(K, y):`
* `def kernel(X, size=0.75, noise=0.1, add_noise=False):`
* `def quantiles(path):`
* `def rescale(path):`
* `def read_data(path):`
* `def shuffle_data(path=""):`

Modules used in program: 
* `import scipy.stats as stats`
* `import cPickle as pk`
* `import scipy as sp`
* `import numpy as np`
* `import random`
* `import cPickle as pk`
* `import numpy as np`
* `import random`

## python GPR

Python mysql example: GPR

```python
import random
import numpy as np
import cPickle as pk

def shuffle_data(path=""):
    f = open(path)
    data = f.read().split("\n")
    f.close()
    random.shuffle(data)
    out = open("data", "w")
    for line in data:
        out.write(line)
        out.write("\n")
    out.close()

def read_data(path):
    f = open(path)
    data = f.read().split("\n")
    f.close()
    X,y = [], []
    for line in data:
        if not line:
            continue
        line = line.split(",")
        first = line.pop(0)
        y.append( int(line.pop()) )
        X.append( tuple((float(x) for x in line)) )
    X = np.array(X)
    y = np.array(y)

    Xf = open("X", "w")
    pk.dump(X, Xf)
    Xf.close()
    yf = open("y", "w")
    pk.dump(y, yf)
    yf.close()

def rescale(path):
    X = pk.load(open(path))
    for i in range(X.shape[1]):
        view = X[:,i]
        mean = np.mean(view)
        var = np.var(view)
        view -= mean
        view /= np.sqrt(var)

    Xf = open("X_scaled", "w")
    pk.dump(X, Xf)
    Xf.close()

def quantiles(path):

    def dist_sq(x, y):
        v = x-y
        return np.dot(v, v)

    Q = [50, 100, 500, 900, 950]
    X = pk.load(open(path))
    rows = X.shape[0] - 1
    indices = []
    for _ in xrange(1000):
        i1 = random.randint(0, rows)
        i2 = random.randint(0, rows)
        while i2 == i1:
            i2 = random.randint(0, rows)
        indices.append((i1, i2))

    dists = []
    for i,j in indices:
        dists.append(dist_sq(X[i], X[j]))

    dists = sorted(dists)

    for e in Q:
        print(e, dists[e])

import random
import numpy as np
import scipy as sp
import cPickle as pk
import scipy.stats as stats

def kernel(X, size=0.75, noise=0.1, add_noise=False):
    d = []
    for i in xrange(X.shape[0]):
        v = X[i]
        d.append(np.dot(v,v))
    d = np.array(d).reshape( (len(d), 1) )
    ones = np.ones( d.shape )

    logK = np.dot(d, ones.T) + np.dot (ones, d.T) - 2*np.dot(X, X.T) 
    logK /= -(size ** 2)
    K = np.exp(logK)
    #print("Kernel matrix with L = %s" % size)
    #print(K)
    #pk.dump(K,open("K", "w"))
    return K

def K_inv_y(K, y):
    return np.linalg.solve(K, y)
    
def partition(X, y, p=5):
    rows = X.shape[0]
    partition = rows / p
    cutoff = partition * (p-1)
    Xtrain = X[:cutoff,:]
    ytrain = y[:cutoff]
    Xtest = X[cutoff:,:]
    ytest = y[cutoff:]

    return Xtrain, ytrain, Xtest, ytest

def partition_K(K, p=5):
    rows = K.shape[0]
    partition = rows / p
    cutoff = partition * (p-1)
    return K[:cutoff, :cutoff], K[cutoff:, :cutoff], \
        K[:cutoff, cutoff:], K[cutoff:, cutoff:],
        
def shuffle(X, y):
    indices = np.arange(X.shape[0])
    np.random.shuffle(indices)
    return X[indices], y[indices]

if __name__ == "__main__":
    X = pk.load(open("X_scaled"))
    y = pk.load(open("y"))
    size = [0.44, 0.75, 6.80, 36.3, 52.4]
    noise = [0.01, 0.03, 0.1, 0.3, 1, 3]
    noise = [0.3]
    best = None
    best_error = 1000000000000

    tr_error = []
    te_error = []

    for s in size:
        for n in noise:
            Xc, yc, Xv, yv = partition(X, y, 6)
            error = 0.0
            """
            for _ in xrange(5):
                Xc, yc = shuffle(Xc, yc)
                K = kernel(Xc, size=s, noise=n)
                Xt, yt, Xte, yte = partition(Xc, yc)
                A, C, CT, B = partition_K(K)
                yp = np.dot(C, K_inv_y(A, yt))
                error += np.mean( 0.5 * ((yte-yp) ** 2 ))
            print("Tr: ", (s,n), error/5)
            """
            K = kernel(X, size=s, noise=n)
            Xt, yt, Xte, yte = partition(X, y)
            A, C, CT, B = partition_K(K)
            An = A.copy()
            i = np.arange(A.shape[0])
            An[i,i] += (n ** 2)
            ytp = np.dot(A, K_inv_y(An, yt))
            train_error = np.mean( 0.5 * ((yt-ytp) ** 2 ))
            yp = np.dot(C, K_inv_y(An, yt))
            test_error = np.mean( 0.5 * ((yte-yp) ** 2 ))
            tr_error.append(train_error)
            te_error.append(test_error)
            if test_error < best_error:
                best = (s, n)
                best_error = test_error
            print("Tr: ", (s,n), train_error)
            print("Te: ", (s,n), test_error)
    print(best)
    pk.dump( (size, tr_error, te_error), open("plots", "w") )

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
