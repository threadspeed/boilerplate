---
title: python script Brute%2520Force%2520D20%2520Roll%2520Simulator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Brute%2520Force%2520D20%2520Roll%2520Simulator'


Modules used in program: 
* `import random`

## python Brute%2520Force%2520D20%2520Roll%2520Simulator

Python example: Brute%2520Force%2520D20%2520Roll%2520Simulator

```python
#Import random module

import random
#Create a variable with a TRUE value

rolling = True
#Create a while loop that rolls until the first digit is 2 or less and the second digit is 10 or less

# while rolling is true
while rolling:
    # create x, a random number between 0 and 99
    x = random.randint(0, 99)
    # create y, a random number between 0 and 99
    y = random.randint(0, 99)
    # if x is less than 2 and y is between 0 and 10
    if x < 2 and 0 < y < 10:
        # Print the outcome
        print('You rolled a {0}{1}.'.format(x, y))
        # And set roll of False
        rolling = False
    # Otherwise
    else:
        # Try again
        print('Trying again.')
 
"""        
Trying again.
Trying again.
Trying again.
Trying again.
Trying again.
Trying again.
Trying again.
Trying again.
Trying again.
You rolled a 13.
"""

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
