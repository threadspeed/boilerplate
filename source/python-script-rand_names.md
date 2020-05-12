---
title: python script rand names (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'rand names'

Functions in program: 
* `def rand_name():`

Modules used in program: 
* `import random`
* `import urllib.request`

## python rand names

Python example: rand names

```python
import urllib.request
import random

word_url = "http://svnweb.freebsd.org/csrg/share/dict/words?view=co&content-type=text/plain"
response = urllib.request.urlopen(word_url)
long_txt = response.read().decode()
words = long_txt.splitlines()

upper_words = [word for word in words if word[0].isupper()]
name_words  = [word for word in upper_words if not word.isupper()]
one_name = ' '.join([name_words[random.randint(0, len(name_words))] for i in range(2)])


def rand_name():
   name = ' '.join([name_words[random.randint(0, len(name_words))] for i in range(2)])
   return name


for n in range(10):
    name = rand_name()
    print(name)

```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
