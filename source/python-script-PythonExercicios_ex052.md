---
title: python script PythonExercicios ex052 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PythonExercicios ex052'


## python PythonExercicios ex052

Python example: PythonExercicios ex052

```python
num = int(input('Digite um número: '))
tot = 0
for c in range(1, num + 1):
    if num % c == 0:
        print('\033[34m', end='')
        tot += 1
    else:
        print('\033[31m', end='')
    print('{} '.format(c), end='')
print('\n\033[mO número {} foi divisível {} vezes'.format(num, tot))
if tot == 2:
    print('O número {} é um número PRIMO!'.format(num))
else:
    print('O número {} não é um número PRIMO!'.format(num))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
