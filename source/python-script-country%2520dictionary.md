---
title: python script country%2520dictionary (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'country%2520dictionary'

Functions in program: 
* `def check_guess(user_guess, country, cc_dict):`
* `def main():`

Modules used in program: 
* `import random`

## python country%2520dictionary

Python example: country%2520dictionary

```python
print("Welcome to the geography quiz!")
import random

def main():
    country_capital_dict ={"Austria":"Vienna", "Slovenia":"Ljubljana", "Russia":"Moscow", "America":"Washington", "Germany":"Berlin", "France":"Paris", "Croatia":"Zagreb"}

    while True:
        random_num = random.randint(0 , 5)
        selected_country = country_capital_dict.keys()[random_num]
        guess = raw_input("What is the capital of %s? " % selected_country)
        check_guess(guess, selected_country, country_capital_dict)

        again=raw_input("Would you like to continue this game? (yes/no) ")
        if again=="no":
           break
           print("END")
           print("!_________________________!")
        elif again=="yes":
            print(guess)

def check_guess(user_guess, country, cc_dict):
    capital = cc_dict[country]

    if user_guess == capital:
        print("Correct! The capital of %s is indeed %s." % (country, capital))
        return True
    else:
        print("Sorry, you are wrong. The capital of %s is %s." % (country, capital))
        return False

if __name__ == "__main__":
    main()



```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
