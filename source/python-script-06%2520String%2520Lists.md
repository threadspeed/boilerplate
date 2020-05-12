---
title: python script 06%2520String%2520Lists (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '06%2520String%2520Lists'


## python 06%2520String%2520Lists

Python example: 06%2520String%2520Lists

```python
line = input("Give me a word or a sentence: ")

j = len(line)
palindrome = True
for cha in line:
    if cha != line[j - 1]:
        palindrome = False
        break
    j = j - 1

[print('It is a palindrome') if palindrome  else print('It is not a palindrome')]

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
