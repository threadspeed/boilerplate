---
title: python script wargame (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'wargame'


Modules used in program: 
* `import random`

## python wargame

Python example: wargame

```python
#Start of the game 
import random

suits=["clubs", "diamonds", "hearts", "spades"]

faces=["2", "3", "4", "5", "6", "7", "8", "9", "10", "Jacks", "Queen", "Kings", "Ace"]

Keep_going= input("Welcome to war if you want to play press v")
#assigning variables
ties= 0

my_score= 0

your_score= 0

hands= 0

keep_going= True

while Keep_going and (hands < 26):

    hands +=1

    my_suits = random.choice(suits)

    my_faces= random.choice(faces)

    your_suits= random.choice (suits)

    your_faces= random.choice (faces)

    print( "you have the", my_faces, "of", my_suits)

    print("the opponent has", your_faces, "of", your_suits)

    if faces.index(your_faces) > faces.index(my_faces):
        
            print(" The oppnent has won the game")
            
            my_score +=0
            
            your_score +=1 + ties
            
            ties=0
            
            print("You:", my_score, "Opponent:", your_score)
            
            Keep_going= input("If you dont want to play anymore click enter if you want to press v")
                
    if faces.index(my_faces) > faces.index(your_faces):
        
            print("you have won the game")
            
            my_score += 1 + ties
            
            your_score +=0
            
            ties = 0
            
            print("You:", my_score, "Opponent:", your_score)
            
            Keep_going= input("If you dont want to play anymore click enter if you want to press v")

    if faces.index(my_faces) == faces.index(your_faces):
        
            print("you have a tie")
            
            my_score += 0
            
            your_score +=0
            
            ties += 1
            
            print("You:", my_score, "Opponent:", your_score)
            
            Keep_going= input("If you dont want to play anymore click enter if you want to press v")
            

    

    






```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
