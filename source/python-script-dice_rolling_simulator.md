---
title: python script dice rolling simulator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dice rolling simulator'


Modules used in program: 
* `import random`

## python dice rolling simulator

Python mysql example: dice rolling simulator

```python
import random
	
min = 1
max = 6

ask = "yes" or "y" or "YES" or "Y"
while (ask == "yes" or ask == "y" or ask == "YES" or ask == "Y"):
	print("Rolling the dices...")
	print("The values are...")
	print(random.randint(min, max))
	print(random.randint(min, max))
	
	ask = str(raw_input("Would you like to roll the dice again? " ))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
