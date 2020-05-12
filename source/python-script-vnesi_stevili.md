---
title: python script vnesi stevili (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'vnesi stevili'


## python vnesi stevili

Python mysql example: vnesi stevili

```python

try:
    a=float(raw_input("Vnesi prvo stevilo: "))
    b=float(raw_input("Vnesi drugo stevilo: "))

#   # napako javimo  uporabniku
    print(a/b)
except ZeroDivisionError:
    print("Deljenje z nulo")
except ValueError:
    print("Uporabi decimalno piko")


a="33,4"
nov_a=a.replace(",", ".")
print(nov_a)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
