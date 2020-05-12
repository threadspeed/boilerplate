---
title: python script rsgen (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rsgen'

Functions in program: 
* `def main():`

Modules used in program: 
* `import random`
* `import argparse`

## python rsgen

Python mysql example: rsgen

```python
#!/usr/bin/env python3.2

#################################################################
# Lim Jiew Meng (A0087884H)
# CS2106 OS Proj 2 : Page Replacement Algorithms
#################################################################

import argparse
import random
from math import floor

class ReferenceStringGenerator:
	# numReferences : total number of page references to generate
	# numPages (P) : num pages in virtual memory
	# workingSet (e) : num pages in working set
	# numPageReferenced (m) : num page referenced 
	# stability: length of stable period (0 - 1)
	def generate(self, numReferences, numPages, workingSet, numPageReferenced, stability):
		rs = ""
		p = random.randint(0, numPages - 1)
		for i in range(floor(numReferences / numPageReferenced)):
			for j in range(numPageReferenced):
				rs += str(random.randint(p, p + workingSet)) + " "
			if random.random() < stability: 
				p = random.randint(0, numPages - 1)
			else:
				p = (p + 1) % numPages
		return rs
	
def main():
    parser = argparse.ArgumentParser(description="Generates reference strings")
    parser.add_argument("--numReferences", metavar="N", type=int, default=100000, help="Number of references to generate")
    parser.add_argument("--numPages", metavar="P", type=int, default=1000, help="Number of pages in virtual memory (# pages)")
    parser.add_argument("--numPageReferenced", metavar="m", type=int, default=100, help="Number of times each page referenced")
    parser.add_argument("--workingSet", metavar="e", type=int, default=50, help="Size of working set (# pages)")
    parser.add_argument("--stability", metavar="t", type=float, default=0.1, help="How stable should the references be. Between 0 - 1")

    args = vars(parser.parse_args())

    # generate reference string
    rsgen = ReferenceStringGenerator()
    rs = rsgen.generate(args['numReferences'], args['numPages'], args['workingSet'], args['numPageReferenced'], args['stability'])
    print(rs)
                        
main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
