---
title: python script ex16.1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex16.1'

Functions in program: 
* `def maker():`
* `def gen():`

Modules used in program: 
* `import string`
* `import random`

## python ex16.1

Python example: ex16.1

```python
import random
import string

strength = int(raw_input("How many characters long would you like your password to be?: "))

def gen():

	let = random.choice(string.ascii_letters)
	num = random.choice(string.digits)
	sym = random.choice(string.punctuation)

gen()

def maker():
	passw = []
	gens = string.ascii_letters + string.digits + string.punctuation
	
	passw = ''.join(random.sample(gens, strength))
		
	print("Your password is: "), passw

maker()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
