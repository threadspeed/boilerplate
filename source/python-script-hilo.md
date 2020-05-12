---
title: python script hilo (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'hilo'


Modules used in program: 
* `import random`

## python hilo

Python example: hilo

```python
import random
suits=["clubs", "diamonds", "hearts", "spades"]

faces=["2", "3", "4", "5", "6", "7", "8", "9", "10", "Jacks", "Queen", "Kings", "Ace"]

Keep_going= input("If you dont want to play anymore click 'q' if you want to keep playing press v")

while Keep_going != 'q':

    my_suits = random.choice(suits)

    my_faces= random.choice(faces)

    your_suits= random.choice (suits)

    your_faces= random.choice (faces)

    print( "you have the", my_faces, "of", my_suits)

    print("the opponent has", your_faces, "of", your_suits)

    if faces.index(your_faces) > faces.index(my_faces):
            print(" The oppnent has won the game")
            Keep_going= input("If you dont want to play anymore click q if you want to press v")
                
    if faces.index(my_faces) > faces.index(your_faces):
            print("you have won the game")
            Keep_going= input("If you dont want to play anymore click q if you want to press v")

    






```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
