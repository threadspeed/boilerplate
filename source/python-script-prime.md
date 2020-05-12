---
title: python script prime (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'prime'

Functions in program: 
* `def primeTable(n):`

## python prime

Python example: prime

```python
def primeTable(n):
  sieve = [True for _ in range(n + 1)]
  i = 2
  while i * i <= n:
      if sieve[i]:
          j = i + i
          while j <= n:
              sieve[j] = False
              j += i
      i += 1
  table = [i for i in range(n + 1) if sieve[i] and i >= 2]
  return table

primes = primeTable(10**7)

head_freq = {}
for prime in primes:
  head = f'{prime}'[0]
  if head_freq.get(head) is None:
    head_freq[head] = 0
  head_freq[head] +=1

for head, freq in sorted(head_freq.items(), key=lambda x:x[0]):
  print(head, freq)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
