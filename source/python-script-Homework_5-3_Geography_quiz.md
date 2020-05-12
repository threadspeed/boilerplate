---
title: python script Homework 5-3 Geography quiz (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'Homework 5-3 Geography quiz'


Modules used in program: 
* `import random`
* `import json`

## python Homework 5-3 Geography quiz

Python mysql example: Homework 5-3 Geography quiz

```python
import json
import random

correct_guesses_in_a_row = 0

with open("European_countries_list.txt", "r") as information_source:
    countries_and_capitals_dict = json.loads(information_source.read())

while True:
    country = random.choice(list(countries_and_capitals_dict.keys()))
    guessed_capital = input("What is the capital of " + country + "? ").lower()

    if guessed_capital.lower() == countries_and_capitals_dict.get(country).lower():
        correct_guesses_in_a_row += 1
        print("That's correct! You have mad geography skillzz! Let's try another one!")
        
    else:
        print("The correct answer is " + countries_and_capitals_dict.get(country) +
              "! Maybe you should practice some more! You got " + str(correct_guesses_in_a_row) +
              " correct guesses in a row!")
        correct_guesses_in_a_row = 0
        answer = input("Do you want to play again and try to set a record? Y/N: ").lower()
        if answer != "y":
            print("See you next time!")
            break



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
