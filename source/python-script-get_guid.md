---
title: python script get guid (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'get guid'

Functions in program: 
* `def get_guid():`
* `def get_guid(style='uuid'):`

Modules used in program: 
* `import uuid`
* `import binascii`
* `import os`

## python get guid

Python example: get guid

```python
import os
import binascii
import uuid
from xid import Xid


def get_guid(style='uuid'):
    """Get a globally unique string for identify things"""
    if style == 'uuid':
        return uuid.uuid4().hex

    if style == 'xid':
        return Xid().string()

    raise RuntimeError('Unsupported guid style: {0}'.format(style))


# Equivalent implementation
def get_guid():
    return binascii.hexlify(os.urandom(16)).decode()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
