---
title: python script get file checksum (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'get file checksum'

Functions in program: 
* `def get_file_checksum(filename):`

Modules used in program: 
* `import os`

## python get file checksum

Python mysql example: get file checksum

```python
import os
from Crypto.Hash import MD5

def get_file_checksum(filename):
    h = MD5.new()
    chunk_size = 8192
    with open(filename, 'rb') as f:
        while True:
            chunk = f.read(chunk_size)
            if len(chunk) == 0:
                break
            h.update(chunk)
    return h.hexdigest()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
