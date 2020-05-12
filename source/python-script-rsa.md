---
title: python script rsa (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rsa'

Functions in program: 
* `def coprime2(a, b):`
* `def isPrime(number):`

Modules used in program: 
* `import math`
* `import random`

## python rsa

Python mysql example: rsa

```python
from math import gcd as bltin_gcd
import random
import math
d=['A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z']

def isPrime(number):
 if number > 1:
  for i in range(2, number):
   if (number % i) == 0:
    return(0)
   else:
    return(1)

def coprime2(a, b):
    return bltin_gcd(a, b) == 1


s= input("Enter plain text:\t")

pt=""
for word in s:
	pt=pt+word
pt=pt.upper()
ct=[]
for i in range (len(pt)):
    ct.append((d.index(pt[i])+1))
print(ct)

#et=''.join(ct)
#print(et)

#primes = [i for i in range(2,1000) if isPrime(i)==1]

p=11#random.choice(primes)
print("Value of p is ",p)
q=13#random.choice(primes)
print("Value of q is ",q)

n=p*q

fn=(p-1)*(q-1)

while True:
	e=random.randint(1,fn)
	if (coprime2(e,fn)):
		break

print("Value of e is ",e)

d = (e*fn + 1) // e

print("Value of d is ",d)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
