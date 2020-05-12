---
title: python script file8 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'file8'

Functions in program: 
* `def fizzbuzz_sort(target):`
* `def next_count(n,f,b,fb):`
* `def make_random_fizzbuzz(start=1,finish=100):`
* `def zbzf(n,f,b,fb):`
* `def fzbz(n):`

Modules used in program: 
* `import random`

## python file8

Python example: file8

```python
import random
def fzbz(n):
  if (n%15) == 0:
    return "FizzBuzz"
  elif (n%5) == 0:
    return "Buzz"
  elif (n%3) == 0:
    return "Fizz"
  else:
    return n

def zbzf(n,f,b,fb):
  n = str(n)
  if n == 'FizzBuzz':
    return fb
  elif n == 'Buzz':
    return b
  elif n == "Fizz":
    return f
  else:
    return int(n)

def make_random_fizzbuzz(start=1,finish=100):
  seq = range(start,finish+1)
  random_fizzbuzz = []
  while seq:
    random_fizzbuzz.append(fzbz(seq.pop(random.randint(0,len(seq)-1))))
  return random_fizzbuzz

def next_count(n,f,b,fb):
  if n == 'FizzBuzz':
    fb += 15
  elif n == 'Buzz':
    if (b%15) == 10:
      b += 10
    else:
      b += 5 
  elif n == "Fizz":
    if (f%15) == 12:
      f += 6
    else:
      f += 3
  return f, b, fb

def fizzbuzz_sort(target):
  limit = len(target)-1
  while limit > 0:
    i = 0
    (f,b,fb) = (3,5,15)
    while i<limit:
      if zbzf(target[i],f,b,fb)>zbzf(target[i+1],f,b,fb):
        target[i], target[i+1] = target[i+1], target[i]
      f,b,fb = next_count(target[i],f,b,fb)
      i += 1
    limit -= 1
  return target
print(fizzbuzz_sort(make_random_fizzbuzz()))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
