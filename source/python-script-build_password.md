---
title: python script build password (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'build password'

Functions in program: 
* `def set_password(txt):`

Modules used in program: 
* `import sensitive`

## python build password

Python mysql example: build password

```python
import sensitive

def set_password(txt):
    # convert the password to numbers
    num = []
    for c in txt:
        num.append(sensitive.the_hash[c])
    length = len(num)
    # set the first char to
    pswd = []
    pswd.append((num[0] + num[length-1]) % 10)
    for i in range(1,length):
        pswd.append((pswd[i-1] + num[i]) % 10)
    final = []
    for n in pswd:
        final.append(sensitive.num_hash[str(n)])
    return ''.join(str(x) for x in final)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
