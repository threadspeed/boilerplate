---
title: python script exercise9 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exercise9'


Modules used in program: 
* `import random `

## python exercise9

Python example: exercise9

```python
import random 

random_num = random.randint(1,9)

while True:
	try: 
		user_number = int(raw_input("Guess my number:"))

	except ValueError:
		print('Only Numerical input\n')
	
	if(user_number > random_num):	
		print('You guessed too high')
	if (random_num > user_number):
		print('You guessed too low')
	if(user_number== random_num):	
		print('You guessed it right!')
		break

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
