---
title: python script practicepython ex11 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'practicepython ex11'

Functions in program: 
* `def check_prime(n):`
* `def get_interger(prompt="Please enter a number: "):`
* `def get_divisors(n):`

## python practicepython ex11

Python example: practicepython ex11

```python
#!/usr/bin/python

def get_divisors(n):
  return [ m for m in range(1, n) if n % m == 0 ]

def get_interger(prompt="Please enter a number: "):
  return int(input(prompt))

def check_prime(n):
  div = get_divisors(n)
  return len(div) > 1




n = get_interger("What interger do you want to check? ")

if check_prime(n):
  print(str(n) + " ain't prime.")
else:
  print(str(n) + " is in fact prime.")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
