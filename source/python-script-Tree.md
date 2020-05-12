---
title: python script Tree (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Tree'

Functions in program: 
* `def main():`
* `def generate(n):`

Modules used in program: 
* `import time `
* `import networkx as nx `
* `import random as rs `
* `import numpy as np `

## python Tree

Python example: Tree

```python
import numpy as np 
import random as rs 
import networkx as nx 
import time 

def generate(n):
	output = []
	output.append(str(10) + "\n")
	for t in range(10):
		output.append(str(n) + "\n")
		g = nx.random_tree(n)
		edges = list(g.edges())
		for i in range(n-1):
			output.append(str(edges[i][0]) + " " + str(edges[i][1]) + "\n")
	return output

def main():
	for f in range(10):
		print("Generating Test Case:",f+1)
		filename = "testcases/input/in" + str(f+1) + ".txt"
		file = open(filename,"a+")
		start = time.time()
		file.writelines(generate(10000))
		end = time.time()
		print("Generated test cases in",end-start,"seconds")
		# generate(10000)

if __name__=="__main__":
	main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
