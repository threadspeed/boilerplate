---
title: python script Hilo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Hilo'


Modules used in program: 
* `import random`

## python Hilo

Python example: Hilo

```python
#Hilo.py
#Creating a game of HiLo
#Importing random module
#Creatung 2 lists: one for suits and one for faces
#Create 2 variables, one for the random selection of faces and one for suites
#print(I have the Ace of Spades)

#use following functions:
#list=array


import random
suits=["Clubs","Diamonds","Hearts","Spades"]
faces=["2","3","4","5","6","7","8","9","10","Jack","Queen","King","Ace"]
reply=input("type [ENTER] to play game or q to quit")
while reply !="q":
    print("")
    my_face=random.choice(faces)
    ur_face=random.choice(faces)

    my_suit=random.choice(suits)
    ur_suit=random.choice(suits)
    
    my_index=faces.index(my_face)
    ur_index=faces.index(ur_face)
    print("I have the",my_face,"of",my_suit,)
    print("You have the",ur_face,"of",ur_suit,)
    
    if my_index > ur_index:
        reply=input("I win! Type [ENTER] to play game or q to quit")
    elif my_index < ur_index:
        reply=input("I lose :( Type [ENTER] to play game or q to quit")
    else:
        reply=input("its a tie. Type [ENTER] to play game or q to quit")
        

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
