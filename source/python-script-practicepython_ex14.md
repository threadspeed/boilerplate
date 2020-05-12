---
title: python script practicepython ex14 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'practicepython ex14'

Functions in program: 
* `def intersection(x,y):`
* `def loop_intersection(x,y):`
* `def set_intersection(x,y):`
* `def loop_dup_clean(l):`
* `def set_dup_clean(l):`

## python practicepython ex14

Python example: practicepython ex14

```python
#!/usr/bin/python

def set_dup_clean(l):
  return list(set(l))

def loop_dup_clean(l):
  r = []
  for x in l:
    if x not in r:
      r.append(x)
  return r

def set_intersection(x,y):
  z = []
  for n in set_dup_clean(x):
    for m in set_dup_clean(y):
      if n == m:
        z.append(n)
  return z

def loop_intersection(x,y):
  z = []
  for n in loop_dup_clean(x):
    for m in loop_dup_clean(y):
      if n == m:
        z.append(n)
  return z

def intersection(x,y):
  z = []
  for n in x:
    for m in y:
      if n == m:
        z.append(n)
  return z

a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
b = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13]

print("List a: " + str(a))
print("List b: " + str(b))
print("List a using set to clean: " + str(set_dup_clean(a)))
print("List a using loop to clean: " + str(loop_dup_clean(a)))
print("List b using set to clean: " + str(set_dup_clean(b)))
print("List b using loop to clean: " + str(loop_dup_clean(b)))
print("Intersection cleaning with set first: " + str(set_intersection(a,b)))
print("Intersection cleaning with loop first: " + str(loop_intersection(a,b)))
print("Intersection cleaning the result via set after: " + str(set_dup_clean(intersection(a,b))))
print("Intersection cleaning the result via loop after: " + str(loop_dup_clean(intersection(a,b))))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
