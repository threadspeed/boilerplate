---
title: python script random-page (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'random-page'

Functions in program: 
* `def display_page(fname):`
* `def pluck_page(book_fname, pagenum):`
* `def page_count(fname):`
* `def random_book():`
* `def display_random_page():`

Modules used in program: 
* `import subprocess`
* `import random`
* `import os`

## python random-page

Python example: random-page

```python
#!/usr/bin/env python

import os
import random
import subprocess


def display_random_page():
    "display a random page from a random book."
    book_fname = random_book()
    pages = page_count(book_fname)
    pagenum = random.randrange(pages) + 1
    print("%s, page %s of %s" % (book_fname, pagenum, pages))
    page_fname = pluck_page(book_fname, pagenum)
    display_page(page_fname)


def random_book():
    "return a random book among the books in the current directory."
    books = [fname for fname in os.listdir('.') if fname.endswith('.pdf')]
    return random.choice(books)


def page_count(fname):
    "return the page count of the given book."
    cmd = "pdfinfo %s | grep Pages: | awk '{print($2}'" % fname)
    output = subprocess.check_output(cmd, shell=True)
    return int(output)


def pluck_page(book_fname, pagenum):
    "extract the given page from the given book."
    cmd = "pdftk %s cat %s output /tmp/random-page.pdf" % (book_fname, pagenum)
    subprocess.check_call(cmd, shell=True)
    return "/tmp/random-page.pdf"


def display_page(fname):
    "display the extracted book page."
    subprocess.check_call("open %s" % fname, shell=True)


if __name__ == "__main__":
    display_random_page()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
