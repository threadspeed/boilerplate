---
title: python script exercise2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exercise2'


## python exercise2

Python mysql example: exercise2

```python

try: 
	age = int(raw_input("Enter a number:"))
except ValueError:
	print(("Non-numerical input not valid"))

try: 
	divider = int(raw_input("Enter a divide by number:"))
except ValueError:
	print(("Non-numerical input not valid"))

if(age%divider==0):
	print('Number', age, 'is divisible by', divider )
	
	
"""
if (age%2==0):
	if(age%4==0):
		print("This number is a multiple of 4!")
	else:
		print("You have entered Even number!")
else:
	print(("You have entered odd number"))
"""	

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
