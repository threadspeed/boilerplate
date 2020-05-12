---
title: python script guessing game one (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'guessing game one'


Modules used in program: 
* `import random`

## python guessing game one

Python example: guessing game one

```python
import random

a = random.randint(1, 9)

ask = int(raw_input("Guess the number: "))

if ask < a:
	print("You guessed too low.")
	
elif ask > a:
	print("You guessed too high.")
	
else:
	print("You win!")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
