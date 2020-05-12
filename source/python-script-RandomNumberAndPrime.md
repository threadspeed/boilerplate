---
title: python script RandomNumberAndPrime (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'RandomNumberAndPrime'

Functions in program: 
* `def main():`
* `def generate(limit):`

Modules used in program: 
* `import sympy`
* `import time `
* `import random as rs `
* `import numpy as np `

## python RandomNumberAndPrime

Python example: RandomNumberAndPrime

```python
import numpy as np 
import random as rs 
import time 
import sympy

def generate(limit):
	output = []
	output.append(str(100000) + "\n")
	for t in range(100000):
		c1 = np.random.randint(1,limit-1)
		c2 = np.random.randint(1,limit-c1)
		x = sympy.randprime(1,10**5)
		y = sympy.randprime(1,10**5)
		output.append(str(c1) + " " + str(c2) + " " + str(x) + " " + str(y) + "\n")
	return output

def main():
	limit = [10**9]*5 + [10**12]*15
	for f in range(20):
		print("Generating Test Case:",f+1)
		filename = "testcases/input/input" + str(f+1) + ".txt"
		file = open(filename,"a+")
		start = time.time()
		file.writelines(generate(limit[f]))
		end = time.time()
		print("Generated test cases in",end-start,"seconds")

if __name__=="__main__":
	main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
