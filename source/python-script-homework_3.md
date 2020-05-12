---
title: python script homework 3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'homework 3'

Functions in program: 
* `def do_work(my_list,error_callback,success_callback):`
* `def error_callback():`
* `def success_callback():`
* `def handle_error():`
* `def handle_success():`
* `def multiply(l):`
* `def keys_process(d):`
* `def list_process(l):`
* `def randomchoice(a):`

Modules used in program: 
* `import random`
* `import random`

## python homework 3

Python mysql example: homework 3

```python
#1 Random errors

import random
list1 = [(1, 2), 'sd', 23]


def randomchoice(a):
	r_value = random.choice(a)
	try:
		int(r_value) / 0
	except ValueError as answer:
	    print('Value error!!! ', answer)	
	except TypeError as answer:
	    print('Type Error!!! ', answer)
	except Exception:
	    raise RuntimeError

randomchoice(list1)	

#2 type(element) and list.sort

import random
list1 = ['avb', 'sd', 23]
list2 = [1, 2, 7, 23, 0]

def list_process(l):
	try:
		for i in l:
			if type(i) == int:
				continue
		l.sort()
		print(l)
	except TypeError as answer:
		raise ValueError
        print('ValueError!')
			
list_process(list2)		    	

#3 dict, keys - to string

dict1 = {1: 2, 23: 'fg', 46: 46, 'as': 23, 'jk':78}

def keys_process(d):
	for i in d.keys():
		d[str(i)] = d.pop(i)
	return d
        print(dict1)			
keys_process(dict1)		

#4 Digits **

list1 = [1, 2, 6, 9, 12]
def multiply(l):
	m = 1
	for i in l:
		m = m * i
	return m	
print(multiply(list1))

#5 

list1 = [1, 2, 9, 4, 5,]
def handle_success():
	print('true')
def handle_error():
	raise ValueError()
	print('false')
def success_callback():
	pass
def error_callback():
	pass
def do_work(my_list,error_callback,success_callback):
	if my_list == sorted(my_list):
		success_callback()
		handle_success()
	else:
		handle_error()
		error_callback()	  	
do_work(list1, error_callback, success_callback)


         

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
