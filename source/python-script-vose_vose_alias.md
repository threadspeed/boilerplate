---
title: python script vose vose alias (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'vose vose alias'


Modules used in program: 
* `import functools`
* `import random`

## python vose vose alias

Python example: vose vose alias

```python
import random
import functools


"""
Reference: http://www.keithschwarz.com/darts-dice-coins/

Initialization:
1 Create arrays Alias and Prob, each of size n.
2 Create two worklists, Small and Large.
3 Multiply each probability by n.

4 For each scaled probability pi:
    4.1 If pi<1, add i to Small.
    4.2 Otherwise (pi≥1), add i to Large.

5 While Small and Large are not empty: (Large might be emptied first)
    5.1 Remove the first element from Small; call it l.
    5.2 Remove the first element from Large; call it g.
    5.3 Set Prob[l]=pl.
    5.4 Set Alias[l]=g.
    5.5 Set pg:=(pg+pl)−1. (This is a more numerically stable option.)
    5.6 If pg<1, add g to Small.
    5.7 Otherwise (pg ≥ 1), add g to Large.

6 While Large is not empty:
    6.1 Remove the first element from Large; call it g.
    6.2 Set Prob[g]=1
7 While Small not empty: This is only possible due to numerical instability.
    7.1 Remove the first element from SmallSmall; call it ll.
    7.2 Set Prob[l] = 1.

Generation:
Generate a fair die roll from an nn-sided die; call the side ii.
Flip a biased coin that comes up heads with probability Prob[i]Prob[i].
If the coin comes up "heads," return ii.
Otherwise, return Alias[i]Alias[i].
"""
class VoseAlias(object):

    def __init__(self, dist):
        """
        :param dist: the distribution a list of tuples with each tuple having a key, weight
        """
        # step 1
        self.Alias = []  # tuples with coin flip results
        self.Prob = []  # unfair coin probability

        # step 2
        Small = []
        Large = []

        # transform incoming dist and normalize

        sum_weight = functools.reduce(lambda x, y: x + y[1], dist, 0.0)

        self.dist = list(map(lambda e: [e[0], float(e[1])/sum_weight], dist))

        self.n = len(self.dist)

        for p in self.dist:
            p[1] *= self.n  # step 3
            if p[1] < 1.0:
                Small.append(p)    # step 4.1
            else:
                Large.append(p)    # step 4.2

        if len(Large) == 0:
            Large = Small[:]
            Small = []

        # step 5

        while len(Small) != 0 and len(Large) !=0:
            small = Small.pop(0)        # step 5.1
            large = Large.pop(0)        # step 5.2
            self.Prob.append(small[1])  # step 5.3
            self.Alias.append((small[0],large[0])) #step 5.4
            large[1]  = large[1]+small[1] - 1
            if large[1] >= 1:
                Large.append(large)     # 5.7
            else:
                Small.append(large)     # 5.6

        while len(Large) != 0:
            large = Large.pop(0)
            self.Prob.append(1)
            self.Alias.append((large[0],large[0]))
            large[1] -= 1
            if large[1] >= 1:
                Large.append(large)   #
            else:
                Small.append(large)   #

    def __call__(self):
        i = random.randint(0, len(self.Prob) - 1)
        if self.Prob[i] >= random.random():
            return self.Alias[i][0]
        else:
            return self.Alias[i][1]




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
