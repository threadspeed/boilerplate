---
title: python script quotes2 (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'quotes2'

Functions in program: 
* `def quote(quote_type, quotes):`

Modules used in program: 
* `import sys`
* `import random`
* `import json`

## python quotes2

Python mysql example: quotes2

```python
import json
import random
import sys


def quote(quote_type, quotes):
    if quote_type in quotes:
        quote_list = quotes[quote_type]
        quote = random.choice(quote_list)
        print(f"\"{quote[1]}\"\n\t-{quote[0]}")
    else:
        print("Quotation could not be found.")


if __name__ == '__main__':
    # Read the data
    with open('quotes.json', 'r') as f:
        quotes = json.load(f)

    while True:
        choices = ', '.join(quotes.keys()) + ', q'
        print("\nChoices: ", choices)
        quote_type = input("What quote do you want to see?")
        if quote_type == 'q':
            quit()
        quote(quote_type, quotes)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
