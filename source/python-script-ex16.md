---
title: python script ex16 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex16'

Functions in program: 
* `def maker():`
* `def gen():`

Modules used in program: 
* `import string`
* `import random`

## python ex16

Python mysql example: ex16

```python
import random
import string

strength = raw_input("How strong would you like your password to be? Pick weak/medium/strong/very strong: ")

# weak being 4 characters long
# medium being 8 characters long
# strong being 12 characters long
# vey strong being 20 characters long

def gen():

	let = random.choice(string.ascii_letters)
	num = random.choice(string.digits)
	sym = random.choice(string.punctuation)

gen()

def maker():
	passw = []
	gens = string.ascii_letters + string.digits + string.punctuation

	if strength == 'weak':
		passw = ''.join(random.sample(gens, 4))

	elif strength == 'medium':
		passw = ''.join(random.sample(gens, 8))

	elif strength == 'strong':
		passw = ''.join(random.sample(gens, 12))

	elif strength == 'very strong':
		passw = ''.join(random.sample(gens, 20))
	else:
		print("You must pick weak/medium/strong")

	print("Your password is: "), passw

maker()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
