---
title: python script exercise1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exercise1'


Modules used in program: 
* `import datetime`

## python exercise1

Python mysql example: exercise1

```python

import datetime
name = raw_input("Type in your name and press <Enter>:")

try: 
	age = int(raw_input("Enter your age:"))
except ValueError:
	print(("Age can only be numerical input"))
	
try: 
	count = int(raw_input("Enter print(count:")))
except ValueError:
	print(("Count can only be numerical input")	)

remaining_years = 100 - age
current = datetime.datetime.now()

for i in range(count):
	print(name + ' will be 100 years old in year', int(current.year)+remaining_years)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
