---
title: python script spectral xmeans demos (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'spectral xmeans demos'

Functions in program: 
* `def test():`
* `def _init(obs,maxk):`
* `def _random_init(obs,maxk,mu=None):`
* `def _xmeans(obs,alpha,mu,dist,idx,iter):`
* `def xmeans(obs,maxk,iter=100,thresh=1e-05,mu=None):`

Modules used in program: 
* `import matplotlib.pyplot as plt`
* `import logging`
* `import itertools`
* `import numpy as np`
* `import random`
* `import scipy`

## python spectral xmeans demos

Python mysql example: spectral xmeans demos

```python
#!/usr/bin/env python
# Programmer : zhuxp
# Date: 
# Last-modified: 01-09-2015, 01:08:30 EST
from numpy import array
import scipy
import random
import numpy as np
from numpy import linalg as LA
from scipy.linalg import eigh
from scipy.cluster.vq import vq,kmeans,whiten
from numpy import random,argmin,compress,equal,log,shape,exp,argmax
import itertools
import logging
import matplotlib.pyplot as plt
def xmeans(obs,maxk,iter=100,thresh=1e-05,mu=None):
    '''
    obs: ndarray
    maxk: int
    '''
    alpha,mu,dist,idx=_random_init(obs,maxk,mu=mu)
    return _xmeans(obs,alpha,mu,dist,idx,iter)
    


def _xmeans(obs,alpha,mu,dist,idx,iter):
    MIN_DIST=1e-05
    (n,d)=shape(obs)
    cutoff=1.01/n
    def _pi(x,i):
        if alpha[i] < cutoff:
            return -float("inf")
        else:
            return log(alpha[i])-d/2.0*log(2.0*3.1415926)-d/2.0*log(dist[i])-1.0/(2*dist[i])*np.sum((x-mu[i])**2)
            #return log(alpha[i])-d/2*log(2*3.1415926)-d/2*log(0.01)-1/(2*0.01)*np.sum((x-mu[i])**2)
    def _p(x):
        p=np.zeros(mu.shape[0])
        for j in xrange(mu.shape[0]):
            p[j]=_pi(x,j)
        return p
    def _isequal(a,b):
        for i,j in itertools.izip(a,b):
            if i!=j:
                return False
        return True
    def _return():
        s=set(idx)
        l=len(s)
        new_mu=[]
        new_dist=[]
        new_alpha=[]
        h={}
        for i,x in enumerate(s):
            new_mu.append(mu[x])
            new_dist.append(dist[x])
            new_alpha.append(alpha[x])
            h[x]=i
        new_idx=[h[i] for i in idx]

        return np.array(new_mu),np.array(new_dist),np.array(new_alpha),np.array(new_idx)
    def _update():
        for i in xrange(mu.shape[0]):
            j=-1
            a=compress(equal(idx,i),obs,0)
            mu[i]=np.ndarray.mean(a,axis=0)
            for d0 in a:
                dist[i]+=np.sum((d0-mu[i])**2)
                j+=1
            if j>-1:
                dist[i]/=(j+1)
            else:
                dist[i]=MIN_DIST
            alpha[i]=float(j+1)/n
        print("update {}".format(count))
        #_print()
        #plt.scatter(b.T[0],b.T[1],c=idx)
        #plt.show()
    def _print():
        print(idx)
        print(mu)
        print(dist)
        print(alpha)
        
    for count in xrange(iter):
        oldidx=np.array(idx)
        for j in xrange(n):
            idx[j]=argmax(_p(obs[j]))
        _update()
        if _isequal(idx,oldidx):
            mu,dist,alpha,idx=_return()
            _print()
            return mu,alpha,dist,idx
    logging.warn("clusering not converged!")
    mu,dist,alpha,idx=_return()
    _print()
    return mu,alpha,dist,idx   

def _random_init(obs,maxk,mu=None):
    from random import sample
    if mu is None:
        mu=np.array(sample(obs,maxk))
    idx,_=vq(obs,mu)
    d=mu.shape[1]
    n=obs.shape[0]
    alpha=np.zeros(mu.shape[0])
    dist=np.ones(mu.shape[0])
    for i in xrange(mu.shape[0]):
        j=-1
        for d0 in compress(equal(idx,i),obs,0):
            dist[i]+=np.sum((d0-mu[i])**2)
            j+=1
        if j>-1:
            dist[i]/=(j+1)
        else:
            dist[i]=MIN_DIST
        alpha[i]=float(j+1)/n
    for i in xrange(mu.shape[0]):
        dist[i]/=d
    return alpha,mu,dist,idx
    
def _init(obs,maxk):
    MIN_DIST=1e-05
    mu,_=kmeans(obs,maxk)
    idx,_=vq(obs,mu)
    d=mu.shape[1]
    n=obs.shape[0]
    alpha=np.zeros(mu.shape[0])
    dist=np.ones(mu.shape[0])
    for i in xrange(mu.shape[0]):
        j=-1
        for d0 in compress(equal(idx,i),obs,0):
            dist[i]+=np.sum((d0-mu[i])**2)
            j+=1
        dist[j]/=(j+1)
        alpha[i]=float(j+1)/n
    for i in xrange(mu.shape[0]):
        dist[i]/=d
    return alpha,mu,dist,idx
            


def test():
    global b
    #p= array([[ 1.9,2.3],[ 1.8,2.4],[ 1.8,2.3],[1.8,2.2],[ 0.1,0.1],[ 0.2,0.2],[ 3.0,0.5],[ 3.1,0.6],[ 3.0,0.4]])
    #xmeans(p,5)
    k=int(random.random()*20)+1
    print(("init k:",k))
    gmu=[]
    gdist=[]
    b=None
    cl=[]
    for i in xrange(k):
        gmu.append((random.random(),1+random.random()))
        gdist.append((0.2*random.random(),0.2*random.random()))
        print("mu_{}".format(i),gmu[-1])
        print("sigma2_{}".format(i),gdist[-1])
        a=random.normal(gmu[-1],gdist[-1],(50,2))
        cl=cl+[i for i0 in xrange(50)]
        if b is None:
            b=a
        else:
            b=np.concatenate((b,a),axis=0)
    l=len(b)
    S0=scipy.spatial.distance.squareform(scipy.spatial.distance.pdist(b,'euclidean'))
    S=1/(S0+1)
    D=sum(S)
    D1=D**-1
    c=D1*S
    value,vector=eigh(c,eigvals=(l-5,l-1))
    rank=range(0,l)
    mu,alpha,dist,idx=xmeans(vector,20)
    xmu,xalpha,xdist,xidx=xmeans(b,20)
    f,axarr=plt.subplots(2,2)
    axarr[0,0].scatter(b.T[0],b.T[1])
    axarr[0,0].set_title("data")
    axarr[0,1].scatter(b.T[0],b.T[1],c=cl)
    axarr[0,1].set_title("generate model k="+str(k))
    axarr[1,1].scatter(b.T[0],b.T[1],c=idx)
    axarr[1,1].set_title("spectral xmeans k="+str(len(mu)))
    axarr[1,0].set_title("xmeans k="+str(len(xmu)))
    axarr[1,0].scatter(b.T[0],b.T[1],c=xidx)
    plt.show()



    
if __name__=="__main__":
    test()







```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
