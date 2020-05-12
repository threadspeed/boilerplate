---
title: python script dragon2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dragon2'


Modules used in program: 
* `import dragonMod`
* `import time`
* `import random`

## python dragon2

Python example: dragon2

```python
#dragon2.py dragon.py modularised
#andyp 23.03.13

import random
import time
import dragonMod

playAgain = 'yes'
while playAgain == 'yes' or playAgain == 'y':

    dragonMod.displayIntro()

    caveNumber = dragonMod.chooseCave()

    dragonMod.checkCave(caveNumber)

    print('Do you want to play again? (yes or no)')
    playAgain = input()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
