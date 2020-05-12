---
title: python script PasswordGenerator (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PasswordGenerator'


Modules used in program: 
* `import random`

## python PasswordGenerator

Python mysql example: PasswordGenerator

```python
# import random  
import random

alphabetUpperCase = list("ABCDEFGHIJKLMNOPQRSTUVWXYZ")
alphabetLowerCase = list("abcdefghijklmnopqrstuvwxyz")
allNumbers = list("1234567890")

passwordLong = input("długość: ")
passwordLong = int(passwordLong)
lettersUpper = input("ABC: (t/n) ")
lettersLower = input("abc: (t/n) ")
specialNumbers = input("123: (t/n) ")

generatedPassword = ""


if lettersUpper == "T" or lettersUpper == "t":
  lettersUpper = True
else:
  lettersUpper = False

if lettersLower == "T" or lettersLower == "t":
  lettersLower = True
else:
  lettersLower = False

if specialNumbers == "T" or specialNumbers == "t":
  specialNumbers = True
else:
  specialNumbers = False

i = 0
while i < passwordLong:
  character = random.sample([1,2,3],1)
  if character == [1]:
    if lettersUpper == True:
      generatedPassword = generatedPassword + random.choice(alphabetUpperCase)
      i+=1
  elif character == [2]:
    if lettersLower == True:
      generatedPassword = generatedPassword + random.choice(alphabetLowerCase)
      i+=1
  elif character == [3]:
    if specialNumbers == True:
      generatedPassword = generatedPassword + random.choice(allNumbers)
      i+=1

print(generatedPassword)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
