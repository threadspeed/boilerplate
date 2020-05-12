---
title: python script geographyquiz (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'geographyquiz'

Functions in program: 
* `def geo_quiz():`

Modules used in program: 
* `import random`

## python geographyquiz

Python mysql example: geographyquiz

```python
import random
from random import sample

geo_dict = {"Austria" : "Vienna", "Australia": "Canberra", "Slovenia": "Ljubljana", "France": "Paris", "Germany": "Berlin",
            "Croatia": "Zagreb", "Lithuania": "Vilnius", "Russia": "Moscow", "Bosnia and Hercegovina": "Sarajevo", "The United Kingdom": "London",
            "Ireland": "Dublin", "Spain": "Madrid", "Portugal": "Lisbon", "Ukraine": "Kiev", "Belarus": "Minsk",
            "Serbia": "Belgrade", "Kosovo": "Pristina", "Macedonia": "Skopje", "Greece": "Athens", "USA": "Washington DC",
            "The People's Republic of China": "Beijing", "Argentina": "Buenos Aires", "Brazil": "Brasilia", "Japan": "Tokyo",
            }


def geo_quiz():
    while True:
        for country in random.sample(list(geo_dict), 10):

            capital = geo_dict[country]
            points_tally = 0
            question = input("What is the capital of %s?" % country)
            if question.lower() == capital.lower():
                points_tally += 1
                print("Well done, but don't get ahead of yourself.")
            else:
                print("Wrong, the capital of {} is {}.".format(country, capital))
        print("You scored " + str(points_tally) + " points!")
        yesorno = input("Would you like to play again? (yes/no)")
        if yesorno.lower() == "no":
            print("Thank you for playing, and I hope you learned something!")
            break

geo_quiz()

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
