---
title: python script write to a file (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'write to a file'


## python write to a file

Python mysql example: write to a file

```python
from sys import argv

script, filename = argv

print("This is a test to see if it can write to the file.")
print("This is an awesome programming language!")
print("If you want to confirm that you want to write to a file, press ENTER.")

raw_input("?")

print("Opening the file...")
target = open(filename, 'w')

statement1 = raw_input("statement 1: ")
statement2 = raw_input("statement 2: ")
statement3 = raw_input("statement 3: ")

print("I'm going to write these to the file.")

target.write(statement1)
target.write("\n")
target.write(statement2)
target.write("\n")
target.write(statement3)
target.write("\n")

target.close()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
