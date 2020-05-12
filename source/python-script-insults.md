---
title: python script insults (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'insults'

Functions in program: 
* `def insult(bot, trigger):`

Modules used in program: 
* `import willie`
* `import random`

## python insults

Python mysql example: insults

```python
# negative reinforcement through insults

#
#
# Sometimes negative reinforcement is the way to go.
# For the times when you need a kick in the pants
# rather than a pat on the back I whipped up this

# insult generator.
# It will churn out more insults then you can shake
# a stick at.

import random
import willie
from willie import module

class insultGenerator(object):
    def __init__(self):
        # setup the lists of insult fodder

        self.nounList = ['dick',
                         'jerk',
                         'nerf herder']
        self.adjectiveList = ['corpulent',
                              'unwashed',
                              'scratchy']
        self.connectorList = ['are one',
                              'are the biggest',
                              'are becoming a']
    def getInsult(self):
        insult = "you"

        # connector phrase
        connector = random.randint(1, len(self.connectorList))
        insult += " " + self.connectorList[connector-1]

        # adjectives
        adjCount = random.randint(2,4)
        random.shuffle(self.adjectiveList)
        for i in xrange(0,adjCount):
            if i != 0:
                insult += ", "

            else:
                insult += " "
            insult += self.adjectiveList[i]

        # ending noun
        noun = random.randint(1,len(self.nounList))
        insult += " " + self.nounList[noun-1]
        return insult

@module.rule('insult?')
def insult(bot, trigger):
    ig = insultGenerator()
    bot.say(ig.getInsult())



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
