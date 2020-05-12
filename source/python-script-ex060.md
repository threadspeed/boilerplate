---
title: python script ex060 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex060'


## python ex060

Python mysql example: ex060

```python
'''from math import factorial
n= int(input('Digite um numero para descobrir seu fatorial: '))
f= factorial(n)
print(f)
'''

n= int(input('Digite um numero para descobrir seu fatorial: '))
c=n
f=1
while c>0:
    print('{}'.format(c), end='')
    print(' x ' if c > 1 else ' = ', end='')
    f=f*c
    c-=1
print('O fatorial é {}'.format(f))



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
