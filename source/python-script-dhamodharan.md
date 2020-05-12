---
title: python script dhamodharan (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'dhamodharan'

Functions in program: 
* `def how_to_save(data, type="csv"):`
* `def get_phone_number():`
* `def get_fake_website():`
* `def get_fake_email():`
* `def get_random_name(my_letters, length):`

Modules used in program: 
* `import json`
* `import csv`
* `import random`
* `import string`
* `import os`
* `import sys`
* `import re`

## python dhamodharan

Python example: dhamodharan

```python
import re
import sys
import os
from faker import Faker
import string
import random
import csv
from dicttoxml import dicttoxml
import json

my_domains = ["hotmail.com", "gmail.com", "aol.com", "mail.com" , "mail.kz", "yahoo.com"]

letters = string.ascii_lowercase[:14]

numbers = range(0,9)

how_many_fake_item_needed = 100

my_website_domains = [".com", ".in", ".au", '.co.in' ,'.net', '.de', '.ch', '.info']

my_website_ssl = ["https://www.", "http://www."]


def get_random_name(my_letters, length):
    return ''.join(random.choice(my_letters) for i in range(length))


def get_fake_email():
    return get_random_name(letters, 7)+'@'+random.choice(my_domains)


def get_fake_website():
    return random.choice(my_website_ssl)+get_random_name(letters, 10)+random.choice(my_website_domains)


def get_phone_number():
    return "+91 9"+''.join(str(random.choice(numbers)) for i in range(9))


def how_to_save(data, type="csv"):
    if type == 'csv':
            try:
                f = open("fake_data.csv", "w")
                w = csv.DictWriter(f, data[1].keys())
                for i in range(1, how_many_fake_item_needed):
                    w.writerow(data[i])
                print("Hey Dude ! Your Csv data is ready.Please Check the file fake_data.csv ")
            except Exception as e:
                print(e)
                print("Something went wrong while saving data in csv")

    if type == "json":
        try:
            with open("fake_data.json", "w") as fp:
                json.dump(data, fp, indent=4)
            print("Hey Dude ! Your Json data saved successfully.please Check the file fake_data.json ")
        except Exception as e:
            print(e)
            print("Something went wrong while saving data in json")

    if type == "xml":
        try:
            data = dicttoxml(list(data.values()), custom_root='ContactInfo', attr_type=False)
            with open("fake_data.xml", "wb") as fp:
                fp.write(data)
            print("Hey Dude ! Your Stuff is ready.please Check the file fake_data.xml ")
        except Exception as e:
            print(e)
            print("Something went wrong while saving data in json")

fake = Faker()
fake_data = {}
for count in range(1, how_many_fake_item_needed):
    fake_data[count] = {}
    fake_data[count]['Name'] = fake.name()
    fake_data[count]['Address'] = fake.address()
    fake_data[count]['IpAddress'] = fake.ipv4_private()
    fake_data[count]['Email-ID'] = get_fake_email()
    fake_data[count]['Website'] = get_fake_website()
    fake_data[count]['PhoneNumber'] = get_phone_number()

how_to_save(fake_data, 'json')
how_to_save(fake_data, 'xml')
how_to_save(fake_data, 'csv')

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
