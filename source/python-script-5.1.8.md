---
title: python script 5.1.8 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '5.1.8'

Functions in program: 
* `def main():`
* `def g(a, b):`

## python 5.1.8

Python mysql example: 5.1.8

```python
"""
Даны действительные числа s,t. Получить g(1.2,s) + g(t,s) - g(2s1,st), где g(a, b) = (a**2 + b**2 - 4*a*b) / (a**2 + 5*a*b + 3*(b**2) + 4*a - b)
"""
def g(a, b):

	return (a**2 + b**2 - 4*a*b) / (a**2 + 5*a*b + 3*(b**2) + 4*a - b)

def main():

	s = float(input("Введите значение s: "))
	t = float(input("Введите значение t: "))
	print(g(1.2, s) + g(t, s) - g(2*s - 1, s*t))

if __name__ == "__main__":
	
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
