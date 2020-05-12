---
title: python script Pass game update (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Pass game update'

Functions in program: 
* `def randomnumber():`
* `def ingame(score):`
* `def loop():             `
* `def for_easy(magic_number):                 `
* `def change(calculator,magic_number):            `

Modules used in program: 
* `import random`

## python Pass game update

Python example: Pass game update

```python
def change(calculator,magic_number):            
    if calculator <= 2:     
        magic_number += 3
    elif calculator <= 8:                   
        magic_number -= 3
    elif calculator <= 15:          #This Function is used to calculate Magic_number,s Position
        magic_number += 2
    elif calculator <= 19:
        magic_number -= 1
    return magic_number;



def for_easy(magic_number):                 
    guess = int(magic_number / 10)  
    if(guess>=1):
        guess='Above 10'
    else:                                       #this function is used to See Hint ( E.g when magic_number is 11 Guess = 1 and when magic_number = 9 guess is 0)
        guess='Below 10'
    return guess;



def loop():             
    rewind =''
    while rewind.lower() != 'yes' and rewind.lower() !='no':
        rewind = input('Play Again And Check Score? ( Yes / No ): ')                          
        if rewind.lower() != 'yes' and rewind.lower() !='no':       #use for outer loop
            print('You Entered Wrong')
    return rewind;

def ingame(score):
    score -= 100  #use for score count
    return score;

def randomnumber():
    magic_number = 20   #function to create random number
    while magic_number > 16 or magic_number < 5:  #to make sure the random number is not a 1 mistake end type
        magic_number=random.randint(1,20)
    return magic_number;

import random
rewind=''
score=2000
count = 1
name=[]
scores=[]
print('_'*50)
print('How to Play:  ')
print('-'*15)
print('1.Guess the Number Correctly...')
print('2.Incorrect Guess will change the Generated Number...( Either Increase it Or Decrease It )')
print('3.The closer you are to the Generated Number the further it will run away...')
print('4.If The Number Goes  below 0 or above 20 You will Lose...')
print('_'*50)
print(''*8)
while rewind.lower() != 'no':       
    print('Enter S to Play | Enter Q to Quit | Enter H To Scores: '.center(100))
    print(('_'*45).center(100))
    play = input()
    chance = 3
    if(play.lower() == 's'):            
        print('You will have 3 Health...'.center(100))
        correct = 1
        print('Generating a New Number'.center(97))
        print(('_'*45).center(100))
        magic_number = randomnumber()
        print(magic_number)
        while correct != 0:
            user_input = int(input('Enter A number From 1 to 20:  '))
            if user_input > 20 or user_input < 0:
                print('Ok..You typed {}..So does it fall between 1 and 20 ?'.format(user_input))
                continue
            calculator = abs(user_input - magic_number)
            
            if(magic_number == user_input):
                print('-'*15)
                print(count,'.Congratulation!! You did it. VERY NICE,He was At Postion=',magic_number)
                print('Your Score=',score)
                print('*'*30)
                name.append(input('Enter Your Name: '))
                scores.append(score)
                print('-'*15)
                correct = 0
                
            elif calculator <= 2:
                magic_number=change(calculator,magic_number)    
                hint = for_easy(magic_number)
                score = ingame(score)
                print('-'*15)
                print(count,'.So close....So it ran 3 steps further.       Hint='+hint)
                print('-'*15)
                count += 1
                print()
                
            elif calculator <= 4:
                magic_number=change(calculator,magic_number)
                hint = for_easy(magic_number)
                score = ingame(score)
                print('-'*15)
                print(count,'.Good Try but He Saw you and he walked 3 step back.     Hint='+hint)
                print('-'*15)
                count += 1
                print()
                
            elif calculator <= 8:
                magic_number=change(calculator,magic_number)
                hint = for_easy(magic_number)
                score = ingame(score)
                print('-'*15)
                print(count,'.Ok, Out Of Luck..he continued to walk 3 steps back.     Hint ='+hint)
                print('-'*15)
                count += 1
                print()
                
            elif calculator <= 12:
                magic_number=change(calculator,magic_number)
                hint = for_easy(magic_number)
                score = ingame(score)
                print('-'*15)
                print(count,'.Ummm , maybe a misfortune... he jumped 2 steps ahead.     Hint ='+hint)
                print('-'*15)
                count += 1
                print()
                
            elif calculator <= 15:
                magic_number=change(calculator,magic_number)
                hint = for_easy(magic_number)
                score = ingame(score)
                print('-'*15)
                print(count,'.Your luck has just expired... He Continued To Jump 2 Steps ahead.    Hint ='+hint)
                print('-'*15)
                count += 1
                print()
                
            elif calculator <= 19:
                magic_number=change(calculator,magic_number)
                hint = for_easy(magic_number)
                score = ingame(score)
                print('-'*15)
                print(count,'.Congratulation!! you failed in style... He walked only 1 step back.    Hint ='+hint)
                print('-'*15)
                count += 1
                print()
            if magic_number > 20 or magic_number < 0:
                chance -= 1
                print('*'*30)
                print('He ran, So Sad ... better Luck Next time......')
                print('Health =',chance)
                print('*'*30)
                print()
                
            if chance == 0:
                print('*'*30)
                print('Bye Bye U lose ....')
                print('*'*30)
                correct = 0
                print()
    elif(play.lower() == 'q'):
        print('Thank You For Playing..')
        rewind = 'no'
    elif(play.lower() == 'h'):
        print('-'*50)
        print('Name:'+(' '*10)+'Scores:')
        for index,string in enumerate(name):
            print(string + (' '*10),end='')
            print(scores[index])
    else:
        print('Please type Correctly..')
    rewind = loop()     
print('Thank You For Playing..')
input()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
