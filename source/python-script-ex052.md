---
title: python script ex052 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'ex052'


## python ex052

Python example: ex052

```python
num=int(input('Digite um numero'))
tot=0
for c in range(1,num+1):
    if num % c == 0 :
        tot+=1
        print('\33[34m',end='')
    else:
        print('\33[m', end='')
    print('{}'.format(c), end=' ')
if tot==2:
    print('\nO numero {} é primo '.format(num))
else:
    print('O numero {} nao é primo'.format(num))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
