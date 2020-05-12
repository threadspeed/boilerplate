---
title: python script fuzzer (snippet)
date: 2020-03-03
tags: ["python"]
---
Python script 'fuzzer'

Functions in program: 
* `def hammer(url):`
* `def spout_urls():`

Modules used in program: 
* `import requests`
* `import string`
* `import random`
* `import logging`

## python fuzzer

Python example: fuzzer

```python
#!/usr/bin/env python2
# -*- coding: utf-8 -*-
""" fuzzing accessible urls.

>>> import random, string
>>> ld = string.letters+string.digits
>>> ld
'ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz0123456789'
>>> len(ld)
62
>>> # this is a permutations problem
>>> 62**6
56800235584
>>> # very feasible to enumerate
"""

import logging
import random
import string
from itertools import islice
from multiprocessing import Pool
from threading import Thread

import requests

logging.basicConfig(level=logging.DEBUG, format='(%(asctime)s %(threadName)-10s) %(message)s', )

ld = string.letters+string.digits

def spout_urls():
    """let's generate some urls"""
    while True:
        urls = "https://www.domain.net/app/{}/success".format(''.join(random.sample(ld,6)))
        yield urls


urls = [x for x in islice(spout_urls(), 1000)]

# def hammer(url, idx):
#     """threading is a PITA to control"""
#     sleep(1)
#     # logging.debug('running')
#     r = requests.get(url)
#     if r.status_code == requests.codes.ok:
#         logging.info("SUCCESS! id: %d status: %d  url: %s " % (idx, int(r.status_code), r.url))
#     else:
#         pass


def hammer(url):
    """let's hammer those urls"""
    r = requests.get(url)
    if r.status_code == requests.codes.ok:
        logging.info("SUCCESS! status: %d  url: %s " % (int(r.status_code), r.url))
    else:
        logging.info("status: %d  url: %s " % (int(r.status_code), r.url))


if __name__ == '__main__':
    p = Pool(10)
    p.map(hammer, urls)

    # for idx, url in enumerate(urls, start=1):
    #     t = Thread(target=hammer, args=(url, idx))
    #     t.start()


```

## Python links

- Learn Python: https://pythonbasics.org/
- Python Tutorial: https://pythonspot.com
