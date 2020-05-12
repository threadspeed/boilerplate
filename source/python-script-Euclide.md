---
title: python script Euclide (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Euclide'

Functions in program: 
* `def ExtendedEuclide(a, b):`
* `def Euclide(a, b):`

## python Euclide

Python mysql example: Euclide

```python
#! /usr/bin/env python
# -*- coding: utf-8 -*-

# Finds the greatest comon divisor of a and b
def Euclide(a, b):
	while a:
		a, b = b%a, a
	return b

# Beside finding the greatest comon divisor of a and b, 
# it also finds integer x and y that satisfy Bésout's identity
def ExtendedEuclide(a, b):
	a1 = 1
	a2 = 0
	a3 = a

	b1 = 0
	b2 = 1
	b3 = b

	while b3 != 0:
		quotient = a3 / b3
		temp1 = a1 - quotient * b1
		temp2 = a2 - quotient * b2
		temp3 = a3 - quotient * b3
		a1 = b1
		a2 = b2
		a3 = b3
		b1 = temp1
		b2 = temp2
		b3 = temp3

		return a1, a2, a3

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
