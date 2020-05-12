---
title: python script winnersOverTime (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'winnersOverTime'

Functions in program: 
* `def countNames():`

Modules used in program: 
* `import os`
* `import sys`
* `import time`
* `import random`

## python winnersOverTime

Python mysql example: winnersOverTime

```python
import random
import time
import sys
import os

def countNames():
    namewritten = ['Tobias','Kjetil','Kasper','Sigmund','Sigve','Preben','Trine','Anders','Adrian','Martin','Ingrid']
    names = [0]*11
    indexlist = range(len(namewritten))
    # print(indexlist)
    with open('winnerss.txt','r+') as infile:
        # while infile:
        #     print(infile.readline())
        for line in infile:
            test = line.strip()
            for (navn,index) in zip(namewritten,indexlist):
                if test == navn:
                    # os.system('say match')
                    names[index] = names[index] + 1
    print(namewritten)
    print(names)
    with open('bardata.txt','w') as outfile:
        for (name,val) in zip(namewritten,names):
            outfile.write(name.strip() + '\t'+ str(val))
            outfile.write('\n')
        # for val in names:
        #     outfile.write(str(val) + ', ')





if __name__ == '__main__':
    countNames()
    os.system('say Elg')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
