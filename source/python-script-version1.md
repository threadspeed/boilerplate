---
title: python script version1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'version1'


Modules used in program: 
* `import random`
* `import cProfile`

## python version1

Python mysql example: version1

```python
import cProfile
import random

class Simulation:
    def run(self):
        self.names = [{'name':'david','spouse':'tyler'},{'name':'tyler','spouse':'david'},
                      {'name':'jon','spouse':'bonnie'},{'name':'bonnie','spouse':'jon'},
                      {'name':'jake','spouse':'caitlin'},{'name':'caitlin','spouse':'jake'},
                      {'name':'dad', 'spouse':'mom'},{'name':'mom','spouse':'dad'}]
        okay = False
        added = []
        assignments = []
        # Continuously attempt to pair until okay
        while not okay:
            # For every single name in the list grab a random one and check against rules
            for name in list(self.names):
                # Rules
                # 1) Can't draw self or spouse
                # 2) Can't add someone twice
                for_name = name
                while (name['name'] == for_name['name'] 
                       or name['spouse'] == for_name['name']
                       or for_name in added):
                    random.seed()
                    for_name = random.choice(self.names)
                # It's okay, add to assignments list and added list
                added.append(for_name)
                assignments.append(' '.join([name['name'],'buys for',for_name['name']]))
                # if we get to mom, we're okay!
                if name['name'] == 'mom':
                    okay = True
        
        print('')
        for s in assignments:
            print(s)

if __name__ == '__main__':
    simulation = Simulation()
    cProfile.run('simulation.run()')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
