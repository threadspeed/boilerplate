---
title: python script nametest (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'nametest'

Functions in program: 
* `def printname():`
* `def namecall():`

## python nametest

Python example: nametest

```python
def namecall():
	text_file = open("names.txt", "r")
	
	lines = []

	lines = text_file.read().split(",")
	
	import random

#	def nameadd():
	n = 0
	name = ""
	while n < 2:
		randomname = random.choice(lines)
		randomname = randomname[:3]
		name += randomname
		n += 1
	return name



def printname():

	trollfirst = namecall().capitalize()
	trolllast = namecall().capitalize()

	trollname = "{} {}".format(trollfirst,trolllast)

	return trollname

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
