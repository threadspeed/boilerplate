---
title: python script exercise6 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exercise6'


## python exercise6

Python mysql example: exercise6

```python

string = (raw_input("Enter a word:"))
r_index = -1

for i in range(len(string)/2):
	if (string[i] == string[r_index]):
		result = 1
	else:
		result = 0
	r_index = r_index -1
	
if result: print(string , ' is a Palindrome' )
else : print(string , 'is NOT a Palindrome')


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
