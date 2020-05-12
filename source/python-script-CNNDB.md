---
title: python script CNNDB (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'CNNDB'

Functions in program: 
* `def main():`
* `def load(path):`
* `def save(path, qpid, clucids, cluster_tab):`
* `def load_mats(path, num, val_or_train):`
* `def processMat(path, img_path, val_or_train):`
* `def cidToFileName(base, cid):`

Modules used in program: 
* `import random`
* `import cv`
* `import os`
* `import h5py`
* `import numpy as np`
* `import scipy.io`

## python CNNDB

Python mysql example: CNNDB

```python
import scipy.io
import numpy as np
import h5py
import os
import cv
import random
from DB import DB
from BaseDB import BaseDB

def cidToFileName(base, cid):
  letters = cid.astype(np.uint32).view("U1").astype(str)
  end = len(cid) - 1
  def arrstr(arr): return reduce(lambda x, y: x+str(y[0]), arr, "")
  return os.path.join(base, \
         arrstr(letters[end-1:end+1]), arrstr(letters[end-3:end-1]), \
         arrstr(letters[end-5:end-3]), arrstr(letters))
         

# Returns pairs that are related and an array of the imagenames + their cluster
def processMat(path, img_path, val_or_train):
  mat = h5py.File(path, "r")
  def processSet(dat):
    cids = np.array([cidToFileName(img_path, np.array(dat[cid[0]])) for cid in dat["cids"]]).transpose()
    cids = np.squeeze(cids)
    cluster = np.squeeze(dat["cluster"])
    pidxs = dat["pidxs"]
    qidxs = dat["qidxs"]
    qpid = np.hstack((pidxs, qidxs))
    clucids = np.vstack((np.array(cids).transpose(), cluster)).transpose()
    return qpid, clucids
  return processSet(mat[val_or_train])

def load_mats(path, num, val_or_train):
  cid_120_p = os.path.join(path, "retrieval-SfM-" + str(num) + "k-imagenames-clusterids.mat")
  mat_120_p = os.path.join(path, "retrieval-SfM-" + str(num) + "k.mat")

  cid_120 = scipy.io.loadmat(cid_120_p)
  qpid, clucids = processMat(mat_120_p, os.path.join(path, "images"), val_or_train)

  clusters = np.squeeze(cid_120["cluster"]).transpose()
  cid = np.squeeze(cid_120["cids"][0]).transpose()
  #clusters and cids
  cluster_tab = np.vstack((clusters, cid)).transpose()

  return qpid, clucids, cluster_tab

class CNNDB(DB, BaseDB):
  def __init__(self, path, val_or_train, img_stats, multi):
    BaseDB.__init__(self, "neg", "SimpleDB")
    DB.__init__(self, "unaltered", img_stats, multi)
    self.qpid, self.clucid, _ = load_mats(path, 120, val_or_train)
    self.clusters, self.index, self.counts = np.unique(self.clucid[:,1], return_counts=True, return_index=True)
    self.clusters = self.clusters.astype(float).astype(int)

  def get_pair_path(self, i):
    # always random cause complicated
    q1 = random.randrange(self.clusters.shape[0])
    q2 = random.randrange(self.clusters.shape[0])
    while q1 == q2:
      q2 = random.randrange(self.clusters.shape[0])
    c1 = self.counts[q1]
    c2 = self.counts[q2]

    i1 = self.index[q1]
    i2 = self.index[q2]

    ind1 = random.randrange(int(c1)) + i1
    ind2 = random.randrange(int(c2)) + i2

    return self.clucid[ind1, 0], self.clucid[ind2, 0]
                                                                                   
  def get_positive_pair_path(self, i):                                           
    [i1, i2] = self.qpid[i].astype(int)                                        
    p1 = self.clucid[i1, 0]                                                    
    p2 = self.clucid[i2, 0]                                                    
    return p1, p2

  def get_length(self):
    return 100 # always random, irrelevant

def save(path, qpid, clucids, cluster_tab):
  with open(path, "wb") as f:
    np.savez(f, qpid=qpid, clucids=clucids, cluster_tab=cluster_tab)

def load(path):
  with open(path, "r") as f:
    mat = np.load(f)
    return mat["qpid"], mat["clucids"], mat["cluster_tab"]

def main():
  path = "raw/CNNImgRetrieval"
  qpid, clucids, cluster_tab = load("indexes/cnn_full_120.mat")
  #qpid, clucids, cluster_tab = load_mats(path, 120)
  #save("indexes/cnn_full_120.mat", qpid, clucids, cluster_tab)
  pairs = []
  for i in qpid:
    [i1, i2] = i.astype(int)
    p1 = clucids[i1, 0]
    p2 = clucids[i2, 0]
    pairs.append([p1, p2])
  with open("indexes/cnn_pos.mat", "wb") as f:
    np.save(f, np.array(pairs))
  #print(qpid, clucids, cluster_tab)

if __name__ == "__main__":
  main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
