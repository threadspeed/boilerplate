---
title: python script facebook-dedup (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'facebook-dedup'


Modules used in program: 
* `import random`
* `import csv`
* `import numpy as np`
* `import pandas as pd`
* `import random`
* `import csv`
* `import numpy as np`
* `import pandas as pd`

## python facebook-dedup

Python example: facebook-dedup

```python
import pandas as pd
import numpy as np
import csv
import random


###########RECUPERATION DES RESULTATS############################################

#np.savez('/home/alfard/Documents/Kaggle/Facebook2/result.npz',RESULT)

#RESULTMP=np.load('/home/alfard/Documents/Kaggle/Facebook2/result.npz')

#RESULTMP=RESULTMP['arr_0']


###############################################################################
# Je recupère Id

a=[]

f = open('/home/alfard/Documents/Kaggle/Facebook2/Train.csv',"rb")
#f = open('/home/ubuntu/TrainClean.csv',"rb")
fileopen = csv.reader(f,delimiter=',', quotechar='"')
 
p=0
for row in fileopen:
    a.append([row[0],row[1]])
    #p=p+1
    #print(p)

f.close()

del a[0]

##############################################################################

t=[]

f = open('/home/alfard/Documents/Kaggle/Facebook2/Test.csv',"rb")
#f = open('/home/ubuntu/TrainClean.csv',"rb")
fileopen = csv.reader(f,delimiter=',', quotechar='"')
 
p=0
for row in fileopen:
    t.append([row[0],row[1]])
    #p=p+1
    #print(p)

f.close()

del t[0]

##############################################################################
a=np.array(a,dtype=object)
t=np.array(t,dtype=object)


##############################################################################
#Recherche intersection

intnp=np.intersect1d(a[:,1],t[:,1])
###############################################################################
#' "Specified initialization vector (IV) does not match the block size for this algorithm" using an CryptoStream'

#np.where(a==' "Specified initialization vector (IV) does not match the block size for this algorithm" using an CryptoStream')
# pour a:2941870
#np.where(t==' "Specified initialization vector (IV) does not match the block size for this algorithm" using an CryptoStream')
# pour b:7695860


###ID TRAIN###

ainv=np.column_stack((a[:,1],a[:,0]))
ainvd=dict(ainv)

communIDTrain=[]
for i in range(0,len(intnp)):
    communIDTrain.append(ainvd[intnp[i]])

communIDTrain=np.array(communIDTrain)

#np.where(communIDTrain=='2941870')
#ligne 272979

###############################################################################
###ID TEST###

tinv=np.column_stack((t[:,1],t[:,0]))
tinvd=dict(tinv)

communIDTest=[]
for i in range(0,len(intnp)):
    communIDTest.append(tinvd[intnp[i]])

communIDTest=np.array(communIDTest)

#np.where(communIDTest=='7695860')



#################################################################################
###TAGS OF TRAIN
del a,t
del ainvd,tinvd

np.savez('/home/alfard/Documents/Kaggle/Facebook2/communID.npz',Train=communIDTrain,Test=communIDTest)

#################################################################################
import pandas as pd
import numpy as np
import csv
import random

CommunID=np.load('/home/alfard/Documents/Kaggle/Facebook2/communID.npz')

CommunID.files

CommunIDTrain=CommunID['Train']
CommunIDTest=CommunID['Test']



#######################################################################################
#RECUPERATION DES TAGS DU TRAIN QUI SONT PRESENTS DANS TEST SUITE A LA DEDUPLICATION
#######################################################################################

w=[]

f = open('/home/alfard/Documents/Kaggle/Facebook2/Train.csv',"rb")
#f = open('/home/ubuntu/TrainClean.csv',"rb")
fileopen = csv.reader(f,delimiter=',', quotechar='"')
 
p=0
for row in fileopen:
    w.append([row[0],row[3]])
    #p=p+1
    #print(p)

f.close()

del w[0]

w=dict(w)


TagTrain=[]
for i in range(0,len(CommunIDTest)):
    TagTrain.append(w[CommunIDTrain[i]])

####################################################################################

RESULTUPDATE=np.column_stack((CommunIDTest,TagTrain))

np.savez('/home/alfard/Documents/Kaggle/Facebook2/Resultupdate.npz',RESULTUPDATE)


#http://docs.scipy.org/doc/numpy/reference/routines.array-manipulation.html#joining-arrays

#http://docs.scipy.org/doc/numpy/reference/routines.set.html





































































a=np.array(a,dtype=object)

a=np.dtype(object)

z=dict(a)

#RESULT.files

commun=[]
for i in range(0,100):
    for j in range(0,len(RESULTMP)):
        
        if RESULTMP[i,0]==a[i,0]:
            commun.append(a[i,0])
    print(i)

#############################################################################

al=list(a[:,0])

RESULTMPl=list(RESULTMP[:,0])

commun=list(set(al).intersection(RESULTMPl))













































z=dict(a)

z['3']




t2=[]
for i in range(0,len(t)):
    if len(t[i].split(' '))>2:
        t2.append(t[i].split(' ')[2])
    else:
        t2.append('')









```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
