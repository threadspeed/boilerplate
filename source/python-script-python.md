---
title: python script python (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'python'

Functions in program: 
* `def main():#define a main function in program `

Modules used in program: 
* `import random #import random module `
* `import sys`
* `import script`

## python python

Python example: python

```python
#!/usr/bin/env python 


#Demonstration of Python Workflow Process 
# Use Two Terminal Windows to Write & Debug Simple Python 3 Program 

import script
import sys
import random #import random module 

"""guesser.py, by Megan Joseph adapted from Richard White

This program has the user guess a number between 1 and 100.
"""

def main():#define a main function in program 
# go through commands and execute 

    print(("Guess a number between 1 and 100"))

#    randomNumber = 10 for debugging purposes once randomNumber value is stored in command terminal 
# can store variable randonNumber in Terminal Bash Script 
randomNumber = random.randInt(1,100)

    found = False

    # flag variable to see if they guessed it right

    # block loops through until answer is correct
    while not found: #could use if statement as well 
    userGuess = input ("Your Guess: ")
    if userGuess == randomNumber:
        print(("You got it right!"))
        found = True # tells user they got correct answer 

     # condition if user is wrong 
    elif userGuess > randonNumber:  #else if statement 
        print(("That's not it! Try again. Guess a lower number"))
    else: 
        print(("That's not it! Try again. Guess higher number"))
    
    # get value for user
    #Say goodbye 
print(("Congratulations, you won. Goodbye"))

if __name__== "__main___":
    #if someone runs this program then execute main block 
    main()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
