---
title: python script Demo 10 FileIO (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Demo 10 FileIO'


Modules used in program: 
* `import os`
* `import sys`
* `import random`

## python Demo 10 FileIO

Python mysql example: Demo 10 FileIO

```python
import random
import sys
import os

test_file = open("test.txt","wb")  #"wb" means can write
#Use "ab+" to Read & Append to File (It also opens or creates the file)

print(test_file.mode)
print(test_file.name)

test_file.write(bytes("Write me to the file\n",'UTF-8'))

test_file.close()

test_file = open("test.txt", "r+")   #r+ means read and write

text_in_file = test_file.read()
print(text_in_file)

test_file.close()

os.remove("test.txt")  #before remove the file, you should close it.

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
