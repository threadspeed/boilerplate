---
title: python script pract3 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'pract3'

Functions in program: 
* `def isPrime(num):`

Modules used in program: 
* `import random`
* `import random`

## python pract3

Python mysql example: pract3

```python
import random
import random
def isPrime(num):
    if num > 1:
        for i in range(2,num):
             if (num % i) == 0:
                 return 0
             else:
                 return 1
    else:
        return 0

primes = [i for i in range(1,1000) if isPrime(i)==1]
p = random.choice(primes)
g = random.choice(primes)
print("Value of p is:\t",p)
print("Value of g is:\t",g)
a = random.choice(primes)
b = random.choice(primes)
print("The Private key for Alice is:\t",a)
print("The Private key for Bob is:\t",b)
x=(g**a)%p
y=(g**b)%p
print("Public keys for Alice and Bob are ",x," and ",y," respectively")
print("Public keys are exchanged here")
print("Alice receives public key ",y," and\n Bob receives public key ",x)
ka = (y**a)%p
kb = (x**b)%p
print("Secret keys of Alice and Bob are ",ka," and ",kb," respectively")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
