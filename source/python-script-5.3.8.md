---
title: python script 5.3.8 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '5.3.8'

Functions in program: 
* `def main():`
* `def NewArrays(A):`

Modules used in program: 
* `import random`

## python 5.3.8

Python mysql example: 5.3.8

```python
"""
8. Вычислить с использованием функции min элементы каждой
строки матрицы A(10,20). Результаты формировать в одномерных
массивах C(10) и D(10)
"""

import random

def NewArrays(A):
        
        C = [min(A[i]) for i in range(0, 10)]
        D = [min(A[i]) for i in range(10, 20)]

        return C, D

def main():

	A = [[random.randint(-100, 100) for i in range(10)] for j in range(20)]
	print(NewArrays(A))

if __name__ == "__main__":
	
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
