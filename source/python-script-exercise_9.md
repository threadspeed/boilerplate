---
title: python script exercise 9 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'exercise 9'


## python exercise 9

Python example: exercise 9

```python
#Pratusevich, M. (n.d.). Practice Python. Retrieved from 
#     http://www.practicepython.org/exercise/2014/04/02/09-guessing-game-one.html
#Ask for input

print("Guess a number between 1 and 9. ")
usernum = input()

#Check if number is the same

while usernum != "quit":
    #Import random Number
    import random
    num = random.randint(1, 9)
    if int(usernum) == int(num):
        print("YOU WIN!")
        usernum = input("Guess a random number from 1 to 9 or enter quit to quit. ")
    else:
        print("Sorry, you did not win. ")
        usernum = input("Guess a random number from 1 to 9 or enter quit to quit. ")

print("Goodbye")


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
