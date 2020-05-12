---
title: python script sieveprimes (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'sieveprimes'

Functions in program: 
* `def primes_sieve(limit):`

## python sieveprimes

Python example: sieveprimes

```python
def primes_sieve(limit):
	"""Calculate prime numbers up to limit"""
	a = [True] * limit
	a[0] = a[1] = False

	for (i, isprime) in enumerate(a):
		if isprime:
			yield i 
			for n in xrange(i*i, limit, i):
				a[n] = False

# Using it
limit = 30
prime = primes_sieve(limit)

for i in range(0, limit-2):
	print(next(prime))
	
#2
#3
#5
#7
#11
#13
#17
#19
#23
#29

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
