---
title: python script week 009 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'week 009'

Functions in program: 
* `def preprocess(text):`
* `def fix(text):`
* `def find_years(text):`
* `def find(text):`
* `def create_password():`
* `def any_digits(s):`
* `def birthday():`
* `def check_age(year, month, day):`
* `def ask_mdy(type):`
* `def _ask_again(type):`
* `def ask_year():`
* `def lucky_ticket(ticket):`
* `def _count_str(s):`

Modules used in program: 
* `import re`

## python week 009

Python example: week 009

```python
### 1

def _count_str(s):
    result = 0
    for i in s:
        result += int(i)
    return result

def lucky_ticket(ticket):
    first = ticket[:3]
    second = ticket[3:]
    return _count_str(first) == _count_str(second)

lucky_ticket("123456")
lucky_ticket("123060")

### 2

def ask_year():
    ask = input("Please enter the year you were born:\n")
    if ask.isdigit():
        if len(ask) != 4:
            print("Error. We need it in the following format: YYYY")
            return ask_year()
        else:
            cent = int(ask[:2])
            if 19 > cent or cent > 20:
                print("Error. Or... are you a time traveler?")
                return ask_year()
            else:
                return int(ask)
    else:
        print("Error. It doesn't look like a number.")
        return ask_year()

# ask_year()      
      
### 3

def _ask_again(type):
    print("Error. Something's gone wrong. Try again!")
    return ask_mdy(type)

def ask_mdy(type):
    min_n = 1
    length = 2

    if type == "month":
        max_n = 12
    elif type == "day":
        max_n = 31
    elif type == "year":
        max_n = 20
        min_n - 19
        length = 4

    ask = input("Please enter the %s you were born:\n" % type)

    if ask.isdigit():
        if len(ask) != length:
            return _ask_again(type)
        else:
            ask_int = int(ask[:2])
            if ask_int > max_n or ask_int < min_n:
                return _ask_again(type)
            else:
                if type != "year":
                    return ask_int
                else:
                    return int(ask)
    else:
        return _ask_again(type)

def check_age(year, month, day):
    curr_year = 2017
    curr_month = 11
    curr_day = 15
    
    diff = curr_year - year
    delta = 0
    if curr_month < month or (curr_month == month and curr_day < day):
        delta = -1
    return diff + delta

def birthday():
    print("Please use the correct format: YYYY for year, MM for month, DD for day.")
    year = ask_mdy("year")
    month = ask_mdy("month")
    day = ask_mdy("day")

    # не учитываем високосный год
    if day > 30 and month in [2, 4, 6, 9, 11] or day > 29 and month == 2:
        month = _ask_again("month")
        day = _ask_again("day")
    print(check_age(year, month, day))

# birthday()

### 4

def any_digits(s):
    result = False
    for c in s:
        if c.isdigit():
            result = True
            break
    return result

def create_password():
    passw = input("Please create a password.")
    n = len(passw)
    if 8 <= n <= 16:
        # good
        if not passw.isalnum():
            # good
            if any_digits(passw):
                # good
                if not passw.islower() and not passw.isupper():
                    # good
                    print("Amazing password!")
                else:
                    # bad
                    print("You should use both lowercase and uppercase.")
            else:
                # bad
                print("There should be at least 1 digit in your password.")
        else:
            # bad
            print("Your password should not consist only of letters and digits.")
    else:
        # bad
        print("Your password should be no less than 8 symbols and no more than 16")

# create_password()
        
### 5

def find(text):
    result = ""
    for c in text:
        if c.isalpha():
            result += c
    return result

### 6

import re

def find_years(text):
    print(re.findall("(?:(?<!\d)\d{4}(?!\d))", text))

### 7

text = "Фамилия: Иванов Имя: Иван Номер паспорта: 5678 Серия: 679742"

def fix(text):
    number = "Номер паспорта: "
    seria = "Серия: "
    
    n_st = text.find(number)
    n_len = len(number)

    s_st = text.find(seria)
    s_len = len(seria)

    first = text[n_st + n_len : s_st - 1]
    second = text[s_st + s_len : ]
    
    # print(first)
    # print(second)
    
    if len(first) == 6 and len(second) == 4:
        return text
    else:
        return text[:n_st] + number + second + " " + seria + first

fix(text)
fix(fix(text))

# 8

'''Для этого замените все апострофы на пробел, удалите знаки препинания и переведите текст в нижний регистр.'''

def preprocess(text):
    syms = ".,:-!?"
    text = text.replace("'", " ")
    text = text.lower()
    for c in syms:
        text = text.replace(c, "")
    return text

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
