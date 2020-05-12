---
title: python script weight random naive commented (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'weight random naive commented'

Functions in program: 
* `def populate_choice_domain(**kwargs):`

Modules used in program: 
* `import random`

## python weight random naive commented

Python example: weight random naive commented

```python
import random

#accept an arbitrary amount of 'keyworded arguments'
def populate_choice_domain(**kwargs):

    #create a holding variable
    choice_domain = ''
    
    #iterate over our user's input in pairs (e.g. xo=2)
    for key, value in kwargs.iteritems():
        #we cannot pass a literal space to a python method, so if we 
        #get a key called space, make it into a literal space
        if key == 'space': 
            key = ' '
        
        #python allows you to multiply a string by an int.  let's do that and append that 
        #value onto our holding variable
        # e.g. turn xo=2 into xoxo
        choice_domain += str((key * value))

    #return the result of our for loop from our function
    return choice_domain 
    
#populate our choice list
choices = populate_choice_domain(xo=2, space=1)
    
for i in range(0, 10): 
    #run our function a bunch of times to show that it works
     print(random.choice(choices))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
