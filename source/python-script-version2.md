---
title: python script version2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'version2'


Modules used in program: 
* `import random`
* `import cProfile`

## python version2

Python mysql example: version2

```python
import cProfile
import random

class Simulation2:
    def run(self):
        self.names = [{'name':'david','spouse':'tyler'},{'name':'tyler','spouse':'david'},
                      {'name':'jon','spouse':'bonnie'},{'name':'bonnie','spouse':'jon'},
                      {'name':'jake','spouse':'caitlin'},{'name':'caitlin','spouse':'jake'},
                      {'name':'dad', 'spouse':'mom'},{'name':'mom','spouse':'dad'}]
        self.newnames = list(self.names)
        okay = False
        assignments = []
        # Continuously attempt to pair until okay
        while not okay:
            random.shuffle(self.newnames)
            dictionary = zip(self.names, self.newnames)
            # For every single name in the list grab a random one and check against rules
            for di in dictionary:
                # Rules
                # 1) Can't draw self or spouse
                # 2) Can't add someone twice
                if (di[0]['name'] == di[1]['name']
                    or di[0]['spouse'] == di[1]['name']):
                    assignments = []
                    break
                else:
                    # It's okay, add to assignments list and added list
                    assignments.append(' '.join([di[0]['name'],'buys for',di[1]['name']]))
            # if we get to 8, we're okay!
            if len(assignments) == 8:
                okay = True

        print('')
        for s in assignments:
            print(s)

if __name__ == '__main__':
    simulation2 = Simulation2()
    cProfile.run('simulation2.run()')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
