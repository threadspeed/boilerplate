---
title: python script primality check (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'primality check'

Functions in program: 
* `def is_prime(num):`

## python primality check

Python example: primality check

```python
def is_prime(num):
    divisors = [x for x in range(2, num) if num % x == 0]
    if len(divisors) == 0:
        return True
    else:
        return False

if __name__ == "__main__":
    num = int(input("Enter a number:"))
    if is_prime(num):
        print(str(num) + " is a prime number.")
    else:
        print(str(num) + " is not a prime number.")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
