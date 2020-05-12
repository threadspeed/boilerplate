---
title: python script test02 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'test02'

Functions in program: 
* `def loop02():`

Modules used in program: 
* `import random`
* `import time`
* `import console`

## python test02

Python example: test02

```python
import console
import time
import random

def loop02():
	A = '□ '
	B = '■ '
	n = 0
	a = 1
	b = 10
	r = 0
	
	masu1 = A
	masu2 = B
	
	while n < 10:
		if n % 10 == 0:
			a = 1	
		print(n)	
		b -= 1
		r = random.randint(1,10)
	
		for x in range(10):
			for y in range(10):
			
				if (x==b)&(y==n)|\
				(x==r)&(y==n):
					print(masu2,end='')
					#time.sleep(0.6)
				else:
					print(masu1,end='')
					#time.sleep(0.3)
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
