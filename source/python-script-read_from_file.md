---
title: python script read from file (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'read from file'


## python read from file

Python example: read from file

```python
num_names = 0

with open('nameslist.txt', 'r') as open_file:
	for name in open_file:
		names = name.split()
		
		num_names += len(names)
		
print(num_names)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
