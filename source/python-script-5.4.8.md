---
title: python script 5.4.8 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '5.4.8'

Functions in program: 
* `def main():`
* `def F(n, eps):`

Modules used in program: 
* `import math`

## python 5.4.8

Python example: 5.4.8

```python
"""
8. Найти сумму ряда с точностью eps, общий член которого равен math.log(math.factorial(n)) / (n**2). 
Точность считается достигнутой, если следующий член последовательности меньше заданного eps.
"""
import math

def F(n, eps):

	An = (math.log(math.factorial(n))) / (n**2)
	if An > eps:
		return An + F(n + 1, eps)
	else:
		return 0

def main():

	n = 2
	result = 0
	eps = float(input("Введите эпсилон: "))
	print((F(n, eps)))


if __name__ == "__main__":
	
	main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
