---
title: python script War (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'War'


## python War

Python example: War

```python
again=input("press enter to start or anything else to quit ")

my_score=0
your_score=0
hands=0
tie=0

while (hands<26) and (again==""):
 import random
 hands=hands+1

 suits=["clubs","diamonds","hearts","spades"]
 faces=["2","3","4","5","6","7","8","9","jack","queen","king","ace"]
 

 my_suit=random.choice(suits)
 my_face=random.choice(faces)

 comp_suit=random.choice(suits)
 comp_face=random.choice(faces)

 print("you have" ,my_face, "of" ,my_suit)

 print("I have" ,comp_face, "of" ,comp_suit)

 if faces.index(my_face)<faces.index(comp_face):
    print("I win the round!")
    my_score=my_score+1+tie
    tie=0
 elif faces.index(my_face)>faces.index(comp_face):
     print("you win this round")
     your_score=your_score+1+tie
     tie=0
 elif faces.index(my_face)==faces.index(comp_face) and suits.index(my_suit)<suits.index(comp_suit):
     print("I win the round with the higher suit!")
     my_score=my_score+1+tie
     tie=0
 elif faces.index(my_face)==faces.index(comp_face) and suits.index(my_suit)>suits.index(comp_suit):
     print("you win the round with the higher suit")
     your_score=your_score+1+tie
     tie=0
 elif faces.index(my_face)==faces.index(comp_face) and suits.index(my_suit)==suits.index(comp_suit):
     print("Its a tie")
     tie=tie+1  
 
 print("Your score:" ,your_score, "My score:" ,my_score,)
 print("------------------------------------ Hand" ,hands, "-----------------------------------")
 again=input("press enter to continue or anything else to quit ")

if (my_score>your_score):
 print("I win with" ,my_score, "points")
if (my_score<your_score):
 print("You win with" ,your_score, "points")
if (my_score==your_score):
 print("the over all game is a tie with" ,my_score, "points each")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
