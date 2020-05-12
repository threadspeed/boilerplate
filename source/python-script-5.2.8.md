---
title: python script 5.2.8 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '5.2.8'

Functions in program: 
* `def main():`
* `def Avg(arr):`
* `def MaxElem(arr):`

Modules used in program: 
* `import random`

## python 5.2.8

Python mysql example: 5.2.8

```python
"""
8. Дан одномерный массив, состоящий из N целочисленных
элементов.
8.1. Найти максимальный элемент.
8.2. Вычислить среднеарифметическое элементов массива
"""
import random

def MaxElem(arr):

	maxelem = arr[0]
	for i in range(1, len(arr)):
		if arr[i] > maxelem:
			maxelem = arr[i]

	return maxelem

def Avg(arr):

	avg = 0
	for elem in arr:
		avg += elem
	avg /= len(arr)

	return avg

def main():

	N = int(input("Введите кол-во элементов массива: "))
	arr = [random.randint(1, 100) for i in range(N)]
	print("Максимальный элемент массива: ", MaxElem(arr))
	print("Среднее арифметическое массива: ", Avg(arr))


if __name__ == "__main__":
	
    main()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
