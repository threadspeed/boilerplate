---
title: python script brute force (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'brute force'

Functions in program: 
* `def brute_force(goal):`
* `def random_string(length):`
* `def random_letter():`

Modules used in program: 
* `import random`

## python brute force

Python example: brute force

```python
import random

alphabet = 'abcdefghijklmnopqrstuvwxyz '

def random_letter():
  return alphabet[random.randint(0,len(alphabet)-1)]

def random_string(length):
  return ''.join([random_letter() for i in range(length)])

def brute_force(goal):
  while 1:
    a = random_string(len(goal))
    if a == goal:
      print('Done!')
      break
    else:
      print(a)

if __name__ == '__main__':
  brute_force('to be or not to be')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
