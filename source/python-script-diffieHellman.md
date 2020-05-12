---
title: python script diffieHellman (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'diffieHellman'

Functions in program: 
* `def listOfPrimes(lower,upper):`
* `def randomPrime(lower,upper):`
* `def genKey(pub,priv,p=17):`
* `def genPub(x,g=3,p=17):`

Modules used in program: 
* `import random`

## python diffieHellman

Python example: diffieHellman

```python
import random
from decimal import *
getcontext().prec=100

def genPub(x,g=3,p=17):
	return (g**x)%p #g^x mod p

def genKey(pub,priv,p=17):
	return (pub**priv)%p #pub^priv mod p

def randomPrime(lower,upper):
	primes = listOfPrimes(lower,upper) #Gen primes
	return primes[random.randint(0,len(primes)-1)] #Return random prime from list

def listOfPrimes(lower,upper):
	primes = []
	for num in range(lower,upper+1):#For each number between lower and upper
		prime = True
		for i in range(2,num):#Checks if divisable for all numbers from 2 up to number
			if num%i==0:#If divisable
				prime = False
		if prime:
			primes.append(num)
	return primes

'''p = randomPrime(1000,5000)
g = random.randint(100000,500000)
print('p,g done')
aPr = random.randint(100000,500000)
bPr = random.randint(100000,500000)
print('pr done')
aPu = genPub(aPr,g,p)
bPu = genPub(bPr,g,p)
print('pu done')
aKey = genKey(bPu,aPr,p)
bKey = genKey(aPu,bPr,p)
print('key done')

print('\nnp:',p,'\ng:',g,'\naPr:',aPr,'\nbPr:',bPr,'\naPu:',aPu,'\nbPu:',bPu,'\naKey:',aKey,'\nbKey:',bKey)


g = Decimal(3)
p = Decimal(7)
aPr = Decimal(7) #random.randint(100000,500000))
print(aPr)
aPu = genPub(aPr,g,p)
print(aPu)
key = genKey(aPu,int(input()),p)
print(key)'''


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
