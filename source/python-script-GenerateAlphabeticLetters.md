---
title: python script GenerateAlphabeticLetters (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'GenerateAlphabeticLetters'


Modules used in program: 
* `import string`
* `import random`

## python GenerateAlphabeticLetters

Python example: GenerateAlphabeticLetters

```python
'''
Python test1. You must import only “random” module. No other modules.
 Here is an incomplete command line script “python3 -c "import random; print()"” which you must complete.
 Only within parenthesis of “print” command and nowhere else you must type a one-line code,
  such that this command line script prints a string consisting randomly from the lowercase and uppercase
  alphabetic characters (meaning 2*26 characters from “a” to “z” and from “A” to “Z”).
The length of the random string must be also random from 5 to 25 characters.
'''
import random
import string
from random import randint
list1=(['a','b','c','d','e','f','g','h','i','j','k','l','m','n','o','p','q','r','s','t','u','v','w','x','y','z',
'A','B','C','D','E','F','G','H','I','J','K','L','M','N','O','P','Q','R','S','T','U','V','W','X','Y','Z']
       )

'''
var 1 
for x in range(20):
    line = random.sample(list1 ,randint(5,25))
    line = ''.join(c for c in line if c not in '[],')
    print(line)

var 1 refine to 1 line 
# without import string module 
print(string.ascii_letters)
for x in range(20):
    print(''.join(c for c in (random.sample(list1 ,randint(5,25))) if c not in '[],'))
# with import string module
'''

#print(string.ascii_letters)
#for x in range(20):
# var 2 one line with import string module 
print(''.join(c for c in (random.sample(string.ascii_letters ,randint(5,25))) if c not in '[],'))

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
