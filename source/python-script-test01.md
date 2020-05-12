---
title: python script test01 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test01'

Functions in program: 
* `def loop01():`

Modules used in program: 
* `import random`
* `import time`
* `import console`

## python test01

Python example: test01

```python
import console
import time
import random

def loop01():
	A = '□ '
	B = '■ '
	n = 0
	a = 1
	b = 10
	
	masu1 = A
	masu2 = B
	
	while n < 10:
		if n % 10 == 0:
			a = 1	
		print(n)
		b -= 1	
	
		for x in range(10):
			for y in range(10):
				
				if (x==n)&(y==0)|\
				(x==b)&(y==8)|\
				(x==b-1)&(y==6):
					print(masu2,end='')			
				elif (x==n*2)&(y==6):
					print(masu2,end='')
				elif (x==n-1)&(y==5):
					print(masu2,end='')	
				elif (x==n-2)&(y==7):
					print(masu2,end='')
				else:
					print(masu1,end='')
				if y == 9**a:
					print('')
		n += 1
		print('')
		
		time.sleep(0.3)
		console.clear()

#loop01()			
			


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
