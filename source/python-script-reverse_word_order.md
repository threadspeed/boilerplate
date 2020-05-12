---
title: python script reverse word order (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'reverse word order'

Functions in program: 
* `def reverse_words(text):`

## python reverse word order

Python example: reverse word order

```python
text = str(raw_input("Enter a sentence: "))

def reverse_words(text):
	answer = ''
	temp = ''
	for char in text:
		if char != ' ':
			temp += char
		else:
			answer = temp + ' ' + answer
			temp = ''
	answer = temp + ' ' + answer
	return answer
	
print(reverse_words(text))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
