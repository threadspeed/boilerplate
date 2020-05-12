---
title: python script string-lists (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'string-lists'


## python string-lists

Python example: string-lists

```python
string = input("Enter a string:")
size = int(len(string))
mid = int(size / 2)
flag = True
for index in range(0, mid):
    if string[index] != string[size - index - 1]:
        flag = False
        break
    else:
        continue
if flag:
    print(string + " is a palindrome.")
else:
    print(string + " is not a palindrome.")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
