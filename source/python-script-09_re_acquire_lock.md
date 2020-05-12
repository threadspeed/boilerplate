---
title: python script 09 re acquire lock (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '09 re acquire lock'


Modules used in program: 
* `import threading`

## python 09 re acquire lock

Python example: 09 re acquire lock

```python
import threading

lock = threading.Lock()
print(lock.acquire())
# print(lock.acquire() #block)
print("y")

lock = threading.RLock()
print(lock.acquire())
print(lock.acquire())
print("y")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
