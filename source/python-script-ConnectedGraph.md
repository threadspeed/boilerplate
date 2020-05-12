---
title: python script ConnectedGraph (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ConnectedGraph'

Functions in program: 
* `def main():`
* `def generate(n):`

Modules used in program: 
* `import math`
* `import time `
* `import networkx as nx `
* `import random as rs `
* `import numpy as np `

## python ConnectedGraph

Python example: ConnectedGraph

```python
import numpy as np 
import random as rs 
import networkx as nx 
import time 
import math

def generate(n):
	output = []
	output.append(str(10) + "\n")
	for t in range(10):
		prob = 500000/(n*n)
		g = nx.fast_gnp_random_graph(n,prob)
		while not nx.is_connected(g):
			g = nx.fast_gnp_random_graph(n,prob)
		edges = list(g.edges())
		output.append(str(n) + " " + str(len(edges)) + "\n")
		for i in range(len(edges)):
			output.append(str(edges[i][0]+1) + " " + str(edges[i][1]+1) + "\n")
	return output

def main():
	for f in range(10):
		print("Generating Test Case:",f+1)
		filename = "testcases/input/input" + str(f+1) + ".txt"
		file = open(filename,"a+")
		start = time.time()
		file.writelines(generate(10000))
		# generate(10000)
		end = time.time()
		print("Generated test cases in",end-start,"seconds")

if __name__=="__main__":
	main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
