---
title: python script Random (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Random'


Modules used in program: 
* `import random`

## python Random

Python mysql example: Random

```python
#import random module to generate random numbers.
import random
print("Random numbers between 0 and 10")
#create a empty list
value=[]
#number generates random numbers for 20 times
number=20
for num in range(number):
    number=random.randint(0,10)
    #append function to append vales to the list
    value.append(int(number))
#print(all values that are appended to list)
print(value)
#inRun a variable that is assigned with a boolean value false
inRun=False
#iterations requires to compare vales of list to put them together inside ( ) using inRun variable
for j in range(len(value)-1):
    if inRun:
        if value[j]!=value[j-1]:
            print(")",end=" ")
            inRun=False
    if not inRun:
        if(value[j]==value[j+1]):
            print("(",end=" ")
            inRun=True
    print(value[j],end=" ")
if inRun or not inRun:
    for n in range(len(value)-2,len(value)-1):
        if value[n]==value[n+1]:
            print(value[-1],")",end=" ")
        else:
            if value[n]==value[n-1]:
                print(")",end=" ")
            print(value[-1],end=" ")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
