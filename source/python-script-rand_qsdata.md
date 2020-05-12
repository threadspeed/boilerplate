---
title: python script rand qsdata (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rand qsdata'


Modules used in program: 
* `import copy`
* `import random`
* `import random `

## python rand qsdata

Python mysql example: rand qsdata

```python
import random 
import random
import copy

#first for vanilla_quicksort, second for pivot that is midpoint, and third for random pivot selection 
rand_data = [random.randint(0, 10000) for i in xrange(1000000)]
rand_mid = copy.deepcopy(rand_data)
rand_random = copy.deepcopy(rand_data)


#worst case for qs: reverse-sorted data 

bad_data = sorted([random.randint(0, 10000) for i in xrange(1000000)], reverse = True)
bad_mid = copy.deepcopy(bad_data)
bad_random = copy.deepcopy(bad_data)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
