---
title: python script quotes (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'quotes'

Functions in program: 
* `def quote(quote_type, quotes):`

Modules used in program: 
* `import sys`
* `import random`
* `import json`

## python quotes

Python example: quotes

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
    if len(sys.argv) < 2:
        print("You must have a type of quote.")
        quit()

    quote_type = sys.argv[1]

    # Read the data
    with open('quotes.json', 'r') as f:
        quotes = json.load(f)

    quote(quote_type, quotes)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
