---
title: python script MQ function 2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'MQ function 2'

Functions in program: 
* `def intcheck(question, low, high): # 2nd function as my integer checker`
* `def MQ_statement(statement, char):  # i added this so that i get * on my welcoming message to make it look better`

## python MQ function 2

Python example: MQ function 2

```python
from random import randint # helps with the random number generator


def MQ_statement(statement, char):  # i added this so that i get * on my welcoming message to make it look better
    print()
    print(char*len(statement))
    print(statement)
    print(char * len(statement))
    print()


def intcheck(question, low, high): # 2nd function as my integer checker
    valid = False
    while not valid:
        error = "Whoops PLease enter an integer between {} and {}".format(low, high)
        print('')
        try:
            response = int(input("Valid integers are between {} and {}".format(low, high)))

            if low <= response <= high:
                return response
            else:
                print(error)
                print()
        except ValueError:
            print(error)




right_feed =["nice job", "good job"] # list of responses
wrong_feed =["unlucky", "yikes"]

# intro

#ask the user for their name so in the next compoenent we can store it

welcome_1 = MQ_statement("welcome to my simple math quiz.","*")
welcome_2 = MQ_statement("what is your name?.","*")
welcome_3 = MQ_statement("if you're new to the game remember to press 'Enter' after every answer.","*")
print('')
print('')
name = input('Type name here: ') # stores 'name'
print('')
print('Good luck',name) # says goodluck to the user wile referring to their 'name'



score = 0  # adds score
questionNum = 1 # adds number to question



# prints question 1 to 5

while questionNum <= 10:
    number1 = randint(1, 10)  # random number is generated form 1 to 10
    number2 = randint(1, 10)
    qAns = number1 + number2  # adds the 2 random numbers
    print('')
    print('Question', questionNum)
    print('what is',str(number1) + ' plus', str(number2) + '?') # integer to string
    print('')
    ans1 = intcheck("", 2, 20)
    if ans1 == qAns:
        print('')
        print('correct')

        import random
        feedback = random.choice(right_feed)
        print(feedback)


        score = score + 1
    else:
        print('')
        print('incorrect!')
        import random

        feedback = random.choice(wrong_feed)
        print(feedback)
    print(name + ',' + ' your current score is', score)
    questionNum = questionNum + 1  # adds 1 to the question
    print('')


print('')
# end of quiz
print('quiz is completed')
print('')
print(name + ',' + ' your final score is', score, 'out of 10' )

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
