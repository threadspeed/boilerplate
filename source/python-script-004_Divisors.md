---
title: python script 004 Divisors (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '004 Divisors'


## python 004 Divisors

Python example: 004 Divisors

```python
# Exercise

# Create a program that asks the user for a number and then prints out a list of all the divisors of that number.
# (If you don’t know what a divisor is, it is a number that divides evenly into another number.
# For example, 13 is a divisor of 26 because 26 / 13 has no remainder.)


n = int(input("Give me a number."))

x = range(1, n+1)
ls = []
for i in x:
    if n % i == 0:
        ls.append(i)
print(ls)

# Extra
if len(ls) == 2:
    print(n, "is a Prime number.")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
