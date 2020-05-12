---
title: python script get random string (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'get random string'

Functions in program: 
* `def get_random_string(N=12, allowed_chars=(string.ascii_letters + string.digits)):`
* `def get_random_string(length=12,`

Modules used in program: 
* `import random`
* `import string`
* `import time`
* `import hashlib`
* `import random`

## python get random string

Python example: get random string

```python
import random
import hashlib
import time


def get_random_string(length=12,
                      allowed_chars='abcdefghijklmnopqrstuvwxyz'
                      'ABCDEFGHIJKLMNOPQRSTUVWXYZ0123456789'):
    """
    See also:
        https://github.com/rs/xid (globally unique id generator)
        https://stackoverflow.com/questions/41354205/how-to-generate-a-unique-auth-token-in-python
        https://docs.python.org/3/whatsnew/3.6.html#secrets
    """
    random.seed(
        hashlib.sha256(
            ("%s%s%s" % (
                random.getstate(),
                time.time(),
                'O_O-SECRET_KEY')).encode('utf-8')
        ).digest())
    return ''.join(random.choice(allowed_chars) for i in range(length))


# --- Simple One ---

import string
import random


def get_random_string(N=12, allowed_chars=(string.ascii_letters + string.digits)):
    return ''.join(random.choice(allowed_chars) for _ in range(N))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
