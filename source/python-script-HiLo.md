---
title: python script HiLo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'HiLo'


## python HiLo

Python example: HiLo

```python
again=input("press enter to start or press q to quit ")
while (again!="q"):
 import random

 suits=["clubs","diamonds","hearts","spades"]
 faces=["2","3","4","5","6","7","8","9","jack","queen","king","ace"]


 my_suit=random.choice(suits)
 my_face=random.choice(faces)

 comp_suit=random.choice(suits)
 comp_face=random.choice(faces)

 print("you have" ,my_face, "of" ,my_suit)

 print("I have" ,comp_face, "of" ,comp_suit)

 if faces.index(my_face)<faces.index(comp_face):
    print("I win!")
 elif faces.index(my_face)>faces.index(comp_face):
    print("you win this time")
 elif faces.index(my_face)==faces.index(comp_face) and suits.index(my_suit)<suits.index(comp_suit):
    print("I win with the higher suit!")
 elif faces.index(my_face)==faces.index(comp_face) and suits.index(my_suit)>suits.index(comp_suit):
    print("you win with the higher suit")
 elif faces.index(my_face)==faces.index(comp_face) and suits.index(my_suit)==suits.index(comp_suit):
     print("it's... a tie?")
     
 again=input("press enter to play again or press q to quit ")

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
