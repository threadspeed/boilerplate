---
title: python script 002 Odd or Even (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script '002 Odd or Even'


## python 002 Odd or Even

Python mysql example: 002 Odd or Even

```python
# Exercise

# Ask the user for a number.
# Depending on whether the number is even or odd, print(out an appropriate message to the user.)
# Hint: how does an even / odd number react differently when divided by 2?

# Extras:

# If the number is a multiple of 4, print(out a different message.)
# Ask the user for two numbers: one number to check (call it num) and one number to
# divide by (check). If check divides evenly into num, tell that to the user.
# If not, print(a different appropriate message.)


a = int(input("Give me a number."))

if a == 0:
    print(">>>> 0 is an EVEN number.")
elif a % 2 == 0 and a % 4 == 0:
    print("\n>>>> You entered an EVEN number as well as the MULTIPLE of 4.")  #EXTRA
elif a % 2 == 0:
    print("\n>>>> You entered an EVEN number.")
else:
    print("\n>>>> You entered an ODD number.")

#EXTRAS

num = int(input("\n\nGive me another number A. Let's name it - NUM\n"))
check = int(input("Give me yet another number to divide A. Let's name it - CHECK\n"))

ch = num // check

rem = num % check

if ch % 2 == 0:
    print("Check EVENLY divides NUM. "
          "Because quotient of {} / {} = {} which is even and remainder is {}.".format(num, check, ch, rem))
elif ch % 2 != 0:
    print("Check DOES NOT evenly divides NUM. "
          "Because quotient of {} / {} = {} which is odd and remainder is {}.".format(num, check, ch, rem))


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
