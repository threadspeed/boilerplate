---
title: python script simulation (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'simulation'

Functions in program: 
* `def main():`
* `def draw(names,numbers,toolbar_width):`

Modules used in program: 
* `import os`
* `import sys`
* `import time`
* `import random`

## python simulation

Python mysql example: simulation

```python
import random
import time
import sys
import os

def draw(names,numbers,toolbar_width):
    nnames = len(names)
    n = [0]*nnames
    sys.stdout.write("[%s]" % (" " * toolbar_width))
    sys.stdout.flush()
    sys.stdout.write("\b" * (toolbar_width+1))
    for i in xrange(numbers):
        a = random.randint(0,nnames-1)
        if i%(numbers/toolbar_width) == 0:
            sys.stdout.write('-')
            sys.stdout.flush()
        n[a]+=1
    teller = max(n)
    sys.stdout.write("\n")
    ind = n.index(teller)
    return names[ind],n

def main():
    names = ['Tobias ','Kjetil ','Kasper ','Sigmund','Sigve  ','Preben ','Trine  ','Anders ','Adrian ','Martin ','Ingrid ']
    random.shuffle(names)
    numbers = 10000
    toolbar_width = 50
    # tid = time.time()
    winner,draws = draw(names,numbers,toolbar_width)
    # elapsed = time.time()-tid
    # print('\nVinneren er: %s \n' %winner,)
    # for a,b in zip(names,draws):
        # print(' %s : \t %d' % (a,b))
    # print('\nTime: '+str(elapsed) )
    # svar = raw_input('Is winner present and deserve to win? ')
    # if svar == 'Yes' or svar == 'yes' or svar == 'Y' or svar == 'y':
    with open('winnerss.txt','a') as outfile:
        date = str(time.strftime("%d:%m:%Y"))
        outfile.write('\n'+date +': \t' + winner)
    # iitest = 'Todays winner is: '+str(winner)
    # output = 'say '+str(iitest)
    # os.system(output)

    # else:
    #     main()



if __name__ == '__main__':
    for i in range(20000):
        main()
    os.system('say Elg')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
