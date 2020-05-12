---
title: python script mee9-lvlup randomphrase (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'mee9-lvlup randomphrase'

Functions in program: 
* `def random_phrase(length):`

Modules used in program: 
* `import string`
* `import random`

## python mee9-lvlup randomphrase

Python example: mee9-lvlup randomphrase

```python
import random
import string


def random_phrase(length):
    return ''.join(random.choice(string.ascii_uppercase) for i in range(length))

print(random_phrase(5) + "-" + random_phrase(5) + "-" + random_phrase(5) + "-" + random_phrase(5))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
