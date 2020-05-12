---
title: python script extra (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'extra'

Functions in program: 
* `def derivative(f, h=0.001):`
* `def gcd(a, b):`
* `def is_prime(num):`
* `def DH_exchange(p):`
* `def count_change(amount, coins):`
* `def local_max(lst):`
* `def repetitions(text, k):`

## python extra

Python example: extra

```python
#########################
# (Extra) Python utilities
# By Oz Tamir
#########################

def repetitions(text, k):
	''' Find all repetitions of at least length k in text '''
	def extend_results(text, i, j, k, pairs):
		while (i > 0 and j > 0) and (text[i - 1] == text[j - 1]):
			k += 1
			i -= 1
			j -= 1
		while (i + k < len(text) and j + k < len(text)) and (text[i + k] == text[j + k]):
			k += 1
		pairs.add((i, j, k))

	pairs = set()
	mem = dict()
	for i in range(len(text)):
		results = mem.get(text[i: i + k], [])
		for j in results:
			extend_results(text, i, j, k, pairs)
		results.append(i)
		mem[text[i: i + k]] = results
	return list(pairs)

def local_max(lst):
	''' Find the subset of lst with the highest sum '''
	maxx = lst[0]
	current_sum = subset_start = 0
	bounds = (0, 0)
	for i, val in enumerate(lst):
		current_sum += lst[i]
		if current_sum > maxx:
			maxx = current_sum
			bounds = (subset_start, i)
		elif current_sum < 0:
			current_sum = 0
			s = i + 1
	return bounds, maxx

# -- Count Change
def count_change(amount, coins):
	if amount == 0:
		return 1
	if len(coins) == 0 or amount < 0:
		return 0
	return count_change(amount - coins[-1], coins) + \
			count_change(amount, coins[:-1])

# -- DH
def DH_exchange(p):
	import random
	""" generates a shared DH key """
	g = random.randint(1, p - 1)
	a = random.randint(1, p - 1)
	b = random.randint(1, p - 1)
	x = pow(g, a, p)
	y = pow(g, b, p)
	key_A = pow(y, a, p)
	key_B = pow(x, b, p)
	return key_A ,key_B

# -- Prime testing
def is_prime(num):
  import random
  for i in range(100):
    a = random.randint(1, num - 1)
    if pow(a, num - 1, num) != 1:
      return False
  return True

# -- Eular GCD
def gcd(a, b):
    while b:
        a, b = b, a % b
    return abs(a)

# -- Derivative
def derivative(f, h=0.001):
	return lambda x: (f(x + h) - f(x)) / h


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
