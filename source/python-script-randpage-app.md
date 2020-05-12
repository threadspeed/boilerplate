---
title: python script randpage-app (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'randpage-app'

Functions in program: 
* `def GET_root(methods=['GET']):`
* `def pluck_page(book_fname, pagenum):`
* `def page_count(fpath):`
* `def random_book(path):`

Modules used in program: 
* `import flask`
* `import subprocess`
* `import random`
* `import os`

## python randpage-app

Python example: randpage-app

```python
#!/usr/bin/env python

import os
import random
import subprocess


def random_book(path):
    "return a random book among the books in the current directory."
    books = [fname for fname in os.listdir(path) if fname.endswith('.pdf')]
    return random.choice(books)


def page_count(fpath):
    "return the page count of the given book."
    cmd = "pdfinfo %s | grep Pages: | awk '{print($2}'" % fpath)
    output = subprocess.check_output(cmd, shell=True)
    return int(output)


def pluck_page(book_fname, pagenum):
    "extract the given page from the given book."
    cmd = "pdftk %s cat %s output /tmp/random-page.pdf" % (book_fname, pagenum)
    subprocess.check_call(cmd, shell=True)
    title = "%s, page %s" % (book_fname.split('/')[-1], pagenum)
    cmd = "exiftool -Title=\"%s\" /tmp/random-page.pdf" % title
    subprocess.check_call(cmd, shell=True)
    return "/tmp/random-page.pdf"


import flask
application = flask.Flask(__name__)

@application.route("/")
def GET_root(methods=['GET']):
    books_dir = '/path/to/pdfs/'
    book_fname = random_book(books_dir)
    pages = page_count(books_dir + book_fname)
    pagenum = random.randrange(pages) + 1
    page_fname = pluck_page(books_dir + book_fname, pagenum)
    with open(page_fname) as f:
        pdf = f.read()
    response = flask.make_response(pdf)
    response.headers['Content-Type'] = 'application/pdf'
    response.headers['Content-Disposition'] = \
        'inline; filename=%s' % book_fname
    response.headers["x-filename"] = book_fname
    response.headers["Access-Control-Expose-Headers"] = 'x-filename'
    return response


if __name__ == "__main__":
    application.run('0.0.0.0', debug=False)


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
