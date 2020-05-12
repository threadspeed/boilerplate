---
title: python script Final Game MQ V5 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Final Game MQ V5'

Functions in program: 
* `def intcheck(question, low = None, high = None):            # this checks if the user is using an integer for rounds`
* `def mq_statemnt(statement, char):`

Modules used in program: 
* `import random`

## python Final Game MQ V5

Python example: Final Game MQ V5

```python
# Full Game
# Modules import random
import random

# Functions
# Statement Generator
def mq_statemnt(statement, char):
    print()
    print(char*len(statement))
    print(statement)
    print(char*len(statement))
    print

# Integer Checker
def intcheck(question, low = None, high = None):            # this checks if the user is using an integer for rounds

    # sets up error messages
    if low is not None and high is not None:
        error = "Please enter a whole number that is between {} and {} " \
                "(inclusive)".format(low, high)
    elif low is not None and high is None:
        error = "Please enter a whole number that is more than or "\
                "equal to {}".format(low)
    elif low is None and high is not None:
        error = "Please enter a whole number that is less than or "\
                "equal to {}".format(high)
    else:
        error = "Please enter a whole number (e.g. 1, 3)"
    while True:

        try:
            response = int(input(question))

            # Checks response is not too low
            if low is not None and response < low:
                print(error)
                continue

            # Checks response is not too high
            elif high is not None and response > high:
                print(error)
                continue

            return response

        except ValueError:
            print(error)
            continue

# Main Routine

user_name = input("What is your name? ") # this use to be in the loop I removed it because i feel like it shouldn't ask the second time
print("Hello {}! Welcome to The Math quiz here are the rules".format(user_name))
mq_statemnt("rule 1: Try this test without the help of your teacher", "*")
mq_statemnt("rule 2: You can quit by typing any letter when it is shown", "*")
mq_statemnt("Rule 3: At the end you will have a score", "*")
mq_statemnt("Rule 4: You can restart again but make sure to let others play", "*")

keep_going = ""

while keep_going == "":
    rounds = intcheck("How many Questions Do you want to receive (Suggestion 10)", 1)
    rounds_played = 0
    rights = 0
    wrong = 0
    while rounds_played < rounds:       # Where the Round Loop Begins
        uno = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10"]
        for item in range(1, 25):
            num1 = random.choice(uno)

        dos = ["1", "2", "3", "4", "5", "6", "7", "8", "9", "10"]
        for item in range(1, 25):
            num2 = random.choice(dos)

        sign = ["*", "+", "-"]

        for item in range(1, 15):
            chosen = random.choice(sign)

        question = num1 + chosen + num2
        answer = eval(question)
        print("*****************")
        print("Question {} of {}".format(rounds_played + 1, rounds))      # This does prompt what question they are on (Newly Added)
        print("*****************")
        print()
        if chosen == "*":
            print("{} x {}".format(num1, num2))
        else:
            print(question)
        user_ans = intcheck("Your Answer: ")            # Where the user will answer

        if user_ans == answer:          # this is where the user answer will be checked
            print()
            print("Correct")

            rights += 1     # this adds on to their score

            if wrong > 0:
                print("You Have Gotten {} right! but you got {} wrong".format(rights, wrong)) # This is the standard message to be shown as students can make mistakes
            else:
                print("You Have Gotten {} Correct, and got none wrong You Rock!".format(rights))     # this is to show a good message for students who have gotten all of them right giving them an extra award

            rounds_played += 1      # adds to the round counter

            print()     # this allows spacing to give user space
            print("*********************************")
            print("You have done {} of {} questions".format(rounds_played, rounds))
            print("*********************************")
            print("*****************************************************************")
            print()



        else:       # This is if the user gets the answer wrong
            print()
            print("Incorrect")
            print()
            print("=========================================")
            print("The answer is {} better luck next time {}".format(answer, user_name))
            print("=========================================")

            wrong += 1

            rounds_played += 1

            if rights == 0:

                print("You have gotten {} wrong. Try harder and get one Right".format(wrong)) # this is to encourage them to get answers correct

            else:

                print("You Have Gotten {} right! but you got {} wrong".format(rights, wrong))   # this is the normal message that will be shown to students when they still have
            print()     # this allows spacing to give user space
            print("*********************************")
            print("You have done {} of {} questions".format(rounds_played, rounds))
            print("*********************************")
            print("*****************************************************************")
            print()
        if rounds == rounds_played:     # once all of the rounds have been completed it will do this

            mq_statemnt("Your Results", "*")    # This makes the heading very visible

            print("These are Your results {}".format(user_name))

            print()
            print("****************")
            print("The Correct: {}".format(rights))
            print("****************")
            print()
            print("-----------------")      # instead of using the text decorator I just made it print(statements, that is because my text decor has no .format)
            print("The Incorrect: {}".format(wrong))
            print("-----------------")
            print()
            print("***********************")
            print("Amount of Questions: {}".format(rounds))
            print("***********************")
            print()
            print("You Have Gotten {} out of {} Correct {}".format(rights, rounds, user_name))
            print()

            keep_going = input("Do you want to try again press <enter> or press any key and <enter> to quit")



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
