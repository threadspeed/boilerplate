---
title: python script PraticePython (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'PraticePython'


Modules used in program: 
* `import random`

## python PraticePython

Python example: PraticePython

```python
###########################################################################################################
Name = raw_input("Enter your Name: ")
age= int(input("Enter your Age: "))
Printcount=int(input("How many times to print: "))
Current_year=int(2017)
turnout100is= (100-age)+2017

print(Printcount *("Hello Mr/Ms"+" "+Name+" "+"You are turning 100 by "+str(turnout100is)+ "\n"))
###########################################################################################################

Number = int(raw_input("Enter a Number: "))

if (Number%2)==0:
    print("Number is Even")
else:
    print("Number is Odd")
    

if (Number%4)==0:
    print("Number is multiple of 4")
else:
    print("Number is not multiple of 4")
###########################################################################################################

#from random.py import *

#random.getstate("self")

a = [1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89]
a_less=[]
x=input("Enter a Number")
for i in range(len(a)):
    if(a[i]<x):
        #print("less", a[i])
        a_less.append(a[i])
    else:
        pass#print("more", a[i])

print(a_less)

###########################################################################################################

x=range(2,11)
number=input("Enter a number")
div_list=[]
for i in range(len(x)):
    if (number%x[i])==0:
        div_list.append(x[i])
    else:
        pass

print(div_list)

###########################################################################################################

import random


list_a = random.sample(range(20), 13 )
list_b = random.sample(range(20), 13)
list_c=[]
print(("Random List 1:", list_a))
print(("Random List 2:" ,list_b))

for i in range(len(list_a)):
    for j in range(len(list_b)):
            if list_a[i]==list_b[j]:
                if list_a[i] not in list_c:
                    list_c.append(list_a[i])
            
print(list_c)
###########################################################################################################

name=raw_input("enter a string")
leng=len(name)

name_reversed = name[:-1]

print("Name Reversed= ", name_reversed)

if name==name_reversed:
    print("Pallindrome")
else:
    print("Not a Pallindrome")




```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
