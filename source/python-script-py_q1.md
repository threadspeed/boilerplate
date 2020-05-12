---
title: python script py q1 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'py q1'

Functions in program: 
* `def fibGen2(max):`
* `def fibGen(max):`
* `def foo():`
* `def foo():`
* `def foo():`
* `def xrand(10):`
* `def rand(10):`
* `def dictInsert(key, val, d = {}):`

Modules used in program: 
* `import random`
* `import random`

## python py q1

Python example: py q1

```python
# Balaji Venkataraman's collections (xbalaji@gmail.com)
# python hints/questions


------------------------------------------------------------------------------
# 1: generate a list (L1) of size 10, each having a value 7
print(L1)
[7, 7, 7, 7, 7, 7,7, 7, 7, 7] 

# Answer
# using list comprehension:
L1 = [7 for ix in range(10)]

# pythonic way
L1 = [7]*10

------------------------------------------------------------------------------

# 2
import random

# random.randint(0, 100) <--- generates a random integer between 0 - 99

# generate a list (L2) of size 10, with a random integer between 0 - 99
print(L2)

# Answer
# using map:
L2 =  map(lambda x: random.randint(0, 100), xrange(10))

# using list comprehension
L2 = [random.randint(0, 100) for ix in xrange(10)]

------------------------------------------------------------------------------

# 3
# what is the output of the following at the end of the statement 'print(d')

a = range(20)
b = a[1:10:2]
c = b[1:1:1]
d = a[3:3:3]

print(a)
print(b)
print(c)
print(d)

------------------------------------------------------------------------------

# 4
# convert a string like 
a1 = "abcdefghi"
a2 = ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h', 'i']
a3 = {1: 'a', 2: 'b', 3: 'c', 4: 'd', 5: 'e', 6: 'f', 7: 'g', 8: 'h', 9: 'i'}
a4 = {'a': 1, 'c': 3, 'b': 2, 'e': 5, 'd': 4, 'g': 7, 'f': 6, 'i': 9, 'h': 8}

# Answer:
a2 = list(a1)
a3 = {x: y for x, y  in enumerate(a1, start=1)}
a4 = { k:v for k,v in enumerate(a1, start=1) }


------------------------------------------------------------------------------

# 5
def dictInsert(key, val, d = {}):
	d[key] = val
	return d

a = { 'one' : 1 }
b = dictInsert('two', 2)
c = dictInsert('six', 6, a)
d = dictInsert('ten', 10)

# what is the output of the following at the end of the statement 'print(d')

print(a)
print(b)
print(c)
print(d)

------------------------------------------------------------------------------

# 6
# factorial using reduce
# n! = n * (n-1) * (n-2) ... 1

n = 10
fact = reduce(lambda x, y: x*y, range(1, n+1))
print(fact)

------------------------------------------------------------------------------

# 7
# what is the difference between range() and xrange()

# write method rand() and xrand(), which takes one parameter which is similar
# to range and xrange

# generates a list right away
def rand(10):
    return map(lambda x: random.randint(1, 100), range(10)) 

# using a generator object
def xrand(10):
    for ix in xrange(10):
        yield random.randint(1, 100)

------------------------------------------------------------------------------

# 8
create a list of boolean which alternate for a given range, like
[true, false, true, false, true, false ...]

create a list of boolean where the values are set to 'true' for elements which are exact multiples of a given integer
[true, false, false, false, true, false, false, false, true, false ...]

create a list with all of the same number like 20
[20, 20, 20, 20, 20, 20 ...]

s1 = [20]*10
change odd/even position to a differnt value
s2 = map(lambda x: s1[x] if x%2 else 10, range(len(s1)))

------------------------------------------------------------------------------
# 9: Write a function using generator which generates the following output:

def foo():
    ....
    ....
    ....

for ix in foo():
	print(ix)

1
'a'
the first alphabet is 'a'


# with generator
def foo():
    yield 1
    yield 'a'
    yield "the first alphabet is 'a'"

# without generator
def foo():
    return [1, 'a', "the first alphabet is 'a'"]


------------------------------------------------------------------------------

# 10: sum of squares from a list of integers

L1 = range(1,11)
L1 = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
L2 = [ ix ** 2 for ix in range(1,11)]
L2 = [1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
sum of L1
sum(L1)
sum of L2 using reduce
reduce(lambda x, y: x + y**2, range(1,5))


L3 = map(lambda x: x**2, L1)

L4 = map(lambda x: x**3, xrange(1,11))
L4 = [1, 8, 27, 64, 125, 216, 343, 512, 729, 1000]

L5 = { k:v for k,v in enumerate(map(lambda x: x**3, xrange(1,11))) }
L5 = {0: 1, 1: 8, 2: 27, 3: 64, 4: 125, 5: 216, 6: 343, 7: 512, 8: 729, 9: 1000}

11:
Create a dictionary with all values equal
D1 = { ix:True for ix in xrange(1,11) }
D1 = {1: True, 2: True, 3: True, 4: True, 5: True, 6: True, 7: True, 8: True, 9: True, 10: True}

12:
fibonnoci using generator
def fibGen(max):
	count = 0
	f1, f2 = 0, 1
	while count < max:
		count += 1
		f1, f2 = f2, f1+f2
		yield f1

		
list(fibGen(10))
[1, 1, 2, 3, 5, 8, 13, 21, 34, 55]

Generate a list:
def fibGen2(max):
	f1, f2 = 0, 1
	r = []
	for ix in xrange(max):
		r.append(f1)
		f1, f2 = f2, f1+f2
	return r

fibGen2(10)
[0, 1, 1, 2, 3, 5, 8, 13, 21, 34]



13: create a random string from string library
a = string.digits + string.ascii_letters
a
'0123456789abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'

import random
random.seed(10)
random.sample(a, 20) <-- create a list of 20 characters from list a
"".join(random.sample(a, 20)) <-- joins them to a string

# use reduce to concatanate string

random.seed(10)
b = reduce( lambda x, y:  str(x) + "".join(random.sample(a,10)), range(10))


14: if there are 100 doors which are closed at the start, there are 100 people numbered 1..100, each person visit the door that are in multiple of their order, like person 3, visit doors 3, 6, 9 ... person 7 visit doors 7, 14, 21 ... Whenever a person visit a door, they would close it if it were open and open if it were closed. After all the 100 people visited, which doors will be closed and which will be open?

write a program to simulate this for varying value of number of doors and number of people

[ [jx for jx in range(ix, max+1, ix)] for ix in range(1, max+1)]



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
